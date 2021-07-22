<template>
  <div
    v-if="isShowing"
    ref="interactElement"
    :class="{
      isCurrent: isCurrent,
    }"
    class="card"
    :style="{ transform: transformString }"
  >
    <img :src="`/img/${img}`" />
    <div class="card-wrap">
      <div class="card-text">{{ card }}</div>
      <p>{{ text }}</p>
      <div
        class="card-frame"
        :style="{ opacity: opacity, color: color, border: border }"
      >
        Препарат- {{ count }}
      </div>
    </div>
  </div>
</template>

<script>
import interact from "interact.js";
const ACCEPT_CARD = "cardAccepted";
const REJECT_CARD = "cardRejected";
const SKIP_CARD = "cardSkipped";

export default {
  static: {
    interactMaxRotation: 15,
    interactOutOfSightXCoordinate: 500,
    interactOutOfSightYCoordinate: 600,
    interactYThreshold: 150,
    interactXThreshold: 100,
  },

  props: {
    card: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    img: {
      type: String,
      required: true,
    },
    id: {
      required: true,
    },
    isCurrent: {
      type: Boolean,
      required: true,
    },
  },

  data() {
    return {
      isShowing: true,
      isInteractAnimating: true,
      isInteractDragged: null,
      interactPosition: {
        x: 0,
        y: 0,
        rotation: 0,
      },
      opacity: 0,
      count: 0,
      color: "",
      border: "",
    };
  },

  computed: {
    transformString() {
      if (!this.isInteractAnimating || this.isInteractDragged) {
        const { x, y, rotation } = this.interactPosition;
        return `translate3D(${x}px, ${y}px, 0) rotate(${rotation}deg)`;
      }

      return null;
    },
  },

  mounted() {
    const element = this.$refs.interactElement;

    interact(element).draggable({
      onstart: () => {
        this.isInteractAnimating = false;
      },

      onmove: (event) => {
        
        const {
          interactMaxRotation,
          interactXThreshold,
          interactYThreshold,
        } = this.$options.static;
        const x = this.interactPosition.x + event.dx;
        const y = this.interactPosition.y + event.dy;

        let rotation = interactMaxRotation * (x / interactXThreshold);

        if (rotation > interactMaxRotation) rotation = interactMaxRotation;
        else if (rotation < -interactMaxRotation)
          rotation = -interactMaxRotation;

        this.interactSetPosition({ x, y, rotation });
        if (x > interactXThreshold)
          (this.color = "#169AE4"),
            (this.border = "8px solid #169AE4"),
            (this.count = 2),
            (this.opacity = 1);
        else if (x < -interactXThreshold)
          (this.color = "#8049c7"),
            (this.border = "8px solid #8049c7"),
            (this.count = 1),
            (this.opacity = 1);
        else if (y < interactYThreshold)
          (this.color = "#ffd748"),
            (this.border = "8px solid #ffd748"),
            (this.count = 3),
            (this.opacity = 1);
      },

      onend: () => {
        const { x, y } = this.interactPosition;
        const { interactXThreshold, interactYThreshold } = this.$options.static;
        this.isInteractAnimating = true;

        if (x > interactXThreshold) this.playCard(ACCEPT_CARD);
        else if (x < -interactXThreshold) this.playCard(REJECT_CARD);
        else if (y < interactYThreshold) this.playCard(SKIP_CARD);
        else this.resetCardPosition();
      },
    });
  },

  beforeDestroy() {
    interact(this.$refs.interactElement).unset();
  },

  methods: {
    hideCard() {
      setTimeout(() => {
        this.isShowing = false;
        this.$emit("hideCard", this.card);
      }, 500);
    },

    playCard(interaction) {
      this.opacity = 1;
      const {
        interactOutOfSightXCoordinate,
        interactOutOfSightYCoordinate,
        interactMaxRotation,
      } = this.$options.static;

      this.interactUnsetElement();

      switch (interaction) {
        case ACCEPT_CARD:
          this.interactSetPosition({
            x: interactOutOfSightXCoordinate,
            rotation: interactMaxRotation,
          });
          this.color = "#169AE4";
          this.border = "8px solid #169AE4";
          this.count = 2;
          this.$emit(ACCEPT_CARD);
          break;
        case REJECT_CARD:
          this.interactSetPosition({
            x: -interactOutOfSightXCoordinate,
            rotation: -interactMaxRotation,
          });
          this.color = "#8049C7";
          this.border = "8px solid #8049C7";
          this.count = 1;
          this.$emit(REJECT_CARD);
          break;
        case SKIP_CARD:
          this.interactSetPosition({
            y: -interactOutOfSightYCoordinate,
          });
          this.color = "#FFB903";
          this.border = "8px solid #FFB903";
          this.count = 3;
          this.$emit(SKIP_CARD);
          break;
      }

      this.hideCard();
    },

    interactSetPosition(coordinates) {
      const { x = 0, y = 0, rotation = 0 } = coordinates;
      this.interactPosition = { x, y, rotation };
    },

    interactUnsetElement() {
      interact(this.$refs.interactElement).unset();
      this.isInteractDragged = true;
    },

    resetCardPosition() {
      this.interactSetPosition({ x: 0, y: 0, rotation: 0 });
    },
  },
  watch: {},
};
</script>

<style lang="scss">
.card {
  width: 540px;
  height: 590px;
  opacity: 0;
  position: absolute;
  border-radius: 20px;
  box-shadow: 0px 0px 40px rgba(127, 127, 127, 0.4);
  overflow: hidden;
  img {
    width: 100%;
  }
  &-text {
    color: #8e9ad5;
    font-size: 32px;
    line-height: 39px;
    font-weight: 700;
  }
  &-wrap {
    padding: 15px 50px 0 50px;
  }
  p {
    font-size: 22px;
    line-height: 39px;
    margin: 0;
  }
  &-frame {
    font-size: 52px;
    line-height: 51px;
    position: absolute;
    top: 50%;
    font-weight: 900;

    padding: 30px 20px;
    transform: rotate(-15deg);
    opacity: 0;
  }
}
.card.isCurrent {
  opacity: 1;
  z-index: 1;
  transition: all 1.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.cards {
  border-radius: 20px;
}
</style>
