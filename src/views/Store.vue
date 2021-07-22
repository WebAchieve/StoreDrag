<template>
  <div class="dragStore">
    <div class="dragStore-wrap" v-if="page">
      <button class="mobile-menu" @click="mobile = !mobile" >
      Меню
    </button>
      <div class="sidebar" :class="[mobile ? 'mobile' : '', '']">
        <div class="sidebar-route">
          <button @click="home()">
            <svg
              width="36"
              height="36"
              viewBox="0 0 36 32"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                opacity="0.5"
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M19.414 0.913912C18.633 0.132864 17.3666 0.132862 16.5856 0.913911L1.41401 16.0855C0.154085 17.3454 1.04642 19.4997 2.82823 19.4997H3.00029V29.9997C3.00029 31.1043 3.89572 31.9997 5.00029 31.9997H13.001C14.1056 31.9997 15.001 31.1043 15.001 29.9997V24.0007C15.001 22.8961 15.8965 22.0007 17.001 22.0007H19.001C20.1056 22.0007 21.001 22.8961 21.001 24.0007V29.9997C21.001 31.1043 21.8965 31.9997 23.001 31.9997H31.0003C32.1049 31.9997 33.0003 31.1043 33.0003 29.9997V19.4997H33.1714C34.9532 19.4997 35.8455 17.3454 34.5856 16.0855L19.414 0.913912Z"
                fill="#FF5864"
              />
            </svg>
          </button>
          <button @click="refresh()">
            <svg
              width="36"
              height="36"
              viewBox="0 0 46 36"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M10.9783 14.0807L9.30194 15.0768C10.6327 8.73682 16.2041 4 22.846 4C28.238 4 32.9242 7.11863 35.211 11.6941C35.7048 12.6822 36.9061 13.0828 37.8942 12.589C38.8822 12.0952 39.2828 10.8939 38.789 9.90586C35.8579 4.04118 29.826 0 22.846 0C13.9372 0 6.57769 6.57426 5.22316 15.1469L3.30995 13.4887C2.47527 12.7652 1.21216 12.8554 0.488706 13.6901C-0.234745 14.5248 -0.144574 15.7879 0.690108 16.5113L5.30511 20.5113L6.39586 21.4567L7.63674 20.7193L13.0217 17.5193C13.9713 16.9551 14.2836 15.7279 13.7194 14.7783C13.1551 13.8287 11.9279 13.5164 10.9783 14.0807ZM36.8799 19.8151L35.0217 20.9193C34.0722 21.4836 32.845 21.1713 32.2807 20.2217C31.7164 19.2721 32.0288 18.0449 32.9783 17.4807L38.3633 14.2807L39.6042 13.5433L40.6949 14.4887L45.31 18.4887C46.1446 19.2121 46.2348 20.4752 45.5114 21.3099C44.7879 22.1446 43.5248 22.2348 42.6901 21.5113L40.8933 19.954C39.8978 29.0103 32.0614 36 22.626 36C15.4747 36 9.25717 31.9925 6.22304 26.1178C5.71617 25.1364 6.10085 23.9299 7.08226 23.423C8.06366 22.9161 9.27015 23.3008 9.77702 24.2822C12.1349 28.8475 16.9934 32 22.626 32C29.9702 32 35.9679 26.6578 36.8799 19.8151Z"
                fill="#FFABB1"
              />
            </svg>
          </button>
        </div>
        <div class="parameters">
          <p>Параметры:</p>
          <div class="parameters-wrap">
            <div class="parameters-buttons">
              <svg
                width="60"
                height="60"
                viewBox="0 0 60 60"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M30 60C46.5685 60 60 46.5685 60 30C60 13.4315 46.5685 0 30 0C13.4315 0 0 13.4315 0 30C0 46.5685 13.4315 60 30 60Z"
                  fill="#D9D9D9
"
                />
                <path
                  d="M16.8348 27.4216C19.258 27.4216 21.2224 25.4572 21.2224 23.0341C21.2224 20.6109 19.258 18.6465 16.8348 18.6465C14.4116 18.6465 12.4473 20.6109 12.4473 23.0341C12.4473 25.4572 14.4116 27.4216 16.8348 27.4216Z"
                  fill="#A1A1A1"
                />
                <path
                  d="M43.163 27.4216C45.5861 27.4216 47.5505 25.4572 47.5505 23.0341C47.5505 20.6109 45.5861 18.6465 43.163 18.6465C40.7398 18.6465 38.7754 20.6109 38.7754 23.0341C38.7754 25.4572 40.7398 27.4216 43.163 27.4216Z"
                  fill="#A1A1A1"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M18.239 44.8507C20.3506 40.4355 24.785 37.4033 29.9978 37.4033C35.2086 37.4033 39.7043 40.4894 41.7617 44.8615L38.307 46.4872C36.8543 43.4004 33.6718 41.2215 29.9978 41.2215C26.3257 41.2215 23.1916 43.3447 21.6835 46.498L18.239 44.8507Z"
                  fill="#A1A1A1"
                />
                <defs>
                  <linearGradient
                    id="paint0_linear"
                    x1="-4.57276e-07"
                    y1="30.219"
                    x2="60"
                    y2="30.219"
                    gradientUnits="userSpaceOnUse"
                  >
                    <stop stop-color="#D9D9D9" />
                    <stop offset="1" stop-color="#A1A1A1" />
                  </linearGradient>
                </defs>
              </svg>
              <span>{{ sad }}</span>
            </div>
            <div class="parameters-buttons">
              <svg
                width="60"
                height="60"
                viewBox="0 0 60 60"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M30 60C46.569 60 60 46.569 60 30C60 13.431 46.569 0 30 0C13.431 0 0 13.431 0 30C0 46.569 13.431 60 30 60Z"
                  fill="#FD98BB"
                />
                <path
                  d="M16.837 27.422C19.26 27.422 21.224 25.457 21.224 23.034C21.224 20.611 19.26 18.646 16.837 18.646C14.414 18.646 12.449 20.611 12.449 23.034C12.449 25.457 14.414 27.422 16.837 27.422Z"
                  fill="#AB4A62"
                />
                <path
                  d="M43.1629 27.422C45.5859 27.422 47.5509 25.457 47.5509 23.034C47.5509 20.611 45.5859 18.646 43.1629 18.646C40.7399 18.646 38.7749 20.611 38.7749 23.034C38.7749 25.457 40.7399 27.422 43.1629 27.422Z"
                  fill="#AB4A62"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M41.7591 39.0499C39.6471 43.4649 35.2131 46.4969 30.0001 46.4969C24.7891 46.4969 20.2941 43.4109 18.2361 39.0389L21.6911 37.4129C23.1441 40.4999 26.3261 42.6789 30.0001 42.6789C33.6721 42.6789 36.8061 40.5559 38.3151 37.4019L41.7591 39.0499Z"
                  fill="#AB4A62"
                />
                <defs>
                  <linearGradient
                    id="paint0_linear"
                    x1="-1.82537e-07"
                    y1="30"
                    x2="48.077"
                    y2="6.058"
                    gradientUnits="userSpaceOnUse"
                  >
                    <stop stop-color="#FD98BB" />
                    <stop offset="1" stop-color="#FFB2AD" />
                  </linearGradient>
                </defs>
              </svg>
              <span>{{ smile }}</span>
            </div>
            <div class="parameters-buttons">
              <svg
                width="56"
                height="48"
                viewBox="0 0 56 48"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M39.879 0C35.176 0 30.958 2.07502 28 5.40002C25.042 2.07502 20.824 0 16.121 0C7.224 0 0 7.45 0 16.625C0 31.989 28 48 28 48C28 48 56 31.989 56 16.625C56 7.45 48.776 0 39.879 0Z"
                  fill="#FD98BB"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M4 17.291C4 10.015 9.738 4 16.939 4C18.044 4 18.939 4.895 18.939 6C18.939 7.105 18.044 8 16.939 8C12.066 8 8 12.104 8 17.291C8 18.396 7.105 19.291 6 19.291C4.895 19.291 4 18.396 4 17.291Z"
                  fill="#8E9AD5"
                />
                <defs>
                  <linearGradient
                    id="paint0_linear"
                    x1="0"
                    y1="24"
                    x2="41.867"
                    y2="-0.325002"
                    gradientUnits="userSpaceOnUse"
                  >
                    <stop stop-color="#FD98BB" />
                    <stop offset="1" stop-color="#FFB2AD" />
                  </linearGradient>
                </defs>
              </svg>

              <span>{{ hart }}</span>
            </div>
          </div>
        </div>
        <div class="queue">
          <p>Осталось в очереди</p>
          <div class="queue-count">
            <span>{{ length }}</span
            >/5
          </div>
        </div>
      </div>
      <div class="panel">
        <div class="users">
          <div class="users-list">
            <UserItem
              :one="one"
              :two="two"
              :three="three"
              :cards="visibleCards"
              @cardAccepted="handleCardAccepted"
              @cardRejected="handleCardRejected"
              @cardSkipped="handleCardSkipped"
              @hideCard="removeCardFromDeck"
            />
          </div>
        </div>
        <div class="panel-bottom">
          <button class="panel-button" @click="drugOne()">Препарат 1</button>
          <button class="panel-button" @click="drugTwo()">Препарат 2</button>
          <button class="panel-button" @click="drugThree()">Препарат 3</button>
        </div>
      </div>
    </div>
    <div
      class="result"
      :style="{ backgroundImage: 'url(/img/result.jpg' }"
      v-else
    >
      <button class="result-home" @click="home()">
        <svg
          width="36"
          height="36"
          viewBox="0 0 36 32"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            opacity="0.5"
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M19.414 0.913912C18.633 0.132864 17.3666 0.132862 16.5856 0.913911L1.41401 16.0855C0.154085 17.3454 1.04642 19.4997 2.82823 19.4997H3.00029V29.9997C3.00029 31.1043 3.89572 31.9997 5.00029 31.9997H13.001C14.1056 31.9997 15.001 31.1043 15.001 29.9997V24.0007C15.001 22.8961 15.8965 22.0007 17.001 22.0007H19.001C20.1056 22.0007 21.001 22.8961 21.001 24.0007V29.9997C21.001 31.1043 21.8965 31.9997 23.001 31.9997H31.0003C32.1049 31.9997 33.0003 31.1043 33.0003 29.9997V19.4997H33.1714C34.9532 19.4997 35.8455 17.3454 34.5856 16.0855L19.414 0.913912Z"
            fill="#FFFFFF"
          />
        </svg>
      </button>
      <div class="result-content">
        <div class="result-results">
          <div class="result-results__item">
            <h3>{{ Math.ceil((sad / 5) * 100) }}%</h3>
            <span>Препарат 1</span>
          </div>
          <div class="result-results__item">
            <h3>{{ Math.ceil((smile / 5) * 100) }}%</h3>
            <span>Препарат 2</span>
          </div>
          <div class="result-results__item">
            <h3>{{ Math.ceil((hart / 5) * 100) }}%</h3>
            <span>Препарат 2</span>
          </div>
        </div>
        <div class="result-title">
          <span>Ваш результат:</span>
          <h2>"Что я здесь делаю?"</h2>
          <p>
            Это тестовое задание, так что не будем углубляться в глубины проблем
            фармацевтов.
          </p>
        </div>
      </div>
      <button class="result-store" @click="page = !page">
        Попробовать еще
      </button>
    </div>
    
  </div>
</template>
<script>
import UserItem from "../components/app/UserItem.vue";
export default {
  name: "Store",

  data() {
    return {
      mobile: false,
      page: true,
      one: false,
      two: false,
      three: false,
      smile: 0,
      sad: 0,
      hart: 0,
      length: 5,
      info: [],
      visibleCards: [
        {
          img: "User-1.jpg",
          name: "Марія, 19 років",
          text:
            "Бабуся приймає брендовий препарат від болю в суглобах, він допомагає,але занадто дорогий. У Вас є якісний аналог з нижчою ціною? Якщо ні — давайте бренд.",
        },
        {
          img: "User-2.jpg",
          name: "Степан, 61 рік",
          text:
            "Спросоння відсунув гарячий чайник рукою та обпікся. У Вас всі ліки від опіків так і дорогі? Можна хороший препарат недорого?",
        },
        {
          img: "User-3.jpg",
          name: "Любов, 58 років",
          text:
            "Лікар призначив препарат від артеріальної гіпертензії, а бренд дорого коштує. Тому мені потрібен аналог з хорошою ефективністю та приємною ціною.",
        },
        {
          img: "User-4.jpg",
          name: "Олександр, 20 років",
          text:
            "Порекомендуйте ефективний препарат від болю в горлі за розумну ціну.",
        },
        {
          img: "User-5.jpg",
          name: "Ірина, 55 років",
          text:
            "У мене часто невралгії, лікар призначив вітаміни групи В. Мені потрібен якісний аналог за прийнятною ціною.",
        },
      ],
    };
  },
  watch: {
    visibleCards(data) {
      this.length = [...data].length;
      if ([...data].length === 0) {
        this.page = !this.page;
      }
    },
  },
  components: {
    UserItem,
  },
  methods: {
    removeCardFromDeck() {
      this.visibleCards.shift();
    },
    handleCardAccepted() {
      this.smile++;
    },
    handleCardRejected() {
      this.sad++;
    },
    handleCardSkipped() {
      this.hart++;
    },
    drugOne() {
      this.one = !this.one;
    },
    drugTwo() {
      this.two = !this.two;
    },
    drugThree() {
      this.three = !this.three;
    },
    refresh() {
      window.location.reload();
    },
    home() {
      this.$router.push("/");
    },
  },
};
</script>
<style lang="scss">
.dragStore {
  height: 100%;
  width: 100%;
  &-wrap {
    height: 100%;
    display: flex;
    width: 100%;
  }
}
.mobile-menu {
  position: absolute;
  top: 5%;
  right: 5%;
  background: #169ae4;
  border: none;
  outline: none;
  padding: 10px;
  border-radius: 40px;
  color: #fff;
  font-size: 18px;
  z-index: 10;
  display: none;
}
.result {
  height: 100%;
  width: 100%;
  background-repeat: no-repeat;
  background-position: top right;
  background-attachment: fixed;
  background-position: cover;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 50%;
  position: relative;
  &-home {
    background: linear-gradient(63.53deg, #2d8550 16.62%, #5e6ec2 83.38%);
    border-radius: 100px;
    width: 70px;
    height: 70px;
    position: absolute;
    left: 50px;
    top: 70px;
    border: none;
    outline: none;
  }
  &-results {
    display: flex;
    justify-content: space-around;
    color: #424242;
    padding-bottom: 60px;
    border-bottom: 2px solid #d9d9d9;
    &__item {
      text-align: center;
      h3 {
        font-size: 48px;
        line-height: 59px;
        font-weight: 300;
        margin: 0;
        padding-bottom: 10px;
      }
      span {
        font-size: 16px;
        line-height: 20px;
        font-weight: 700;
      }
    }
  }
  &-content {
    width: 40%;
    position: absolute;
    left: 130px;
    top: 26%;
  }
  &-title {
    margin-top: 40px;
    span {
      color: #8e9ad5;
      font-size: 32px;
      line-height: 35px;
      font-weight: 700;
    }
    h2 {
      color: #8e9ad5;
      font-size: 40px;
      line-height: 35px;
      font-weight: 900;
      margin: 0;
      padding-top: 10px;
    }
    p {
      color: #424242;
      font-size: 24px;
      line-height: 29px;
    }
  }
  &-store {
    font-size: 24px;
    line-height: 29px;
    color: #ffffff;
    font-weight: 700;
    position: absolute;
    left: 130px;
    bottom: 80px;
    background: linear-gradient(90deg, #d9d9d9 0%, #a1a1a1 100%);
    border-radius: 100px;
    width: 280px;
    height: 60px;
    border: none;
    outline: none;
  }
}
.sidebar {
  background: linear-gradient(63.53deg, #2d8550 16.62%, #5e6ec2 83.38%);
  min-width: 470px;
  height: 100%;
  position: relative;
  transition: 0.5s ease;
  &-route {
    padding: 70px 0 0 50px;
    button {
      background: #fff;
      border-radius: 50%;
      width: 70px;
      height: 70px;
      margin-right: 38px;
      border: none;
      outline: none;
    }
  }
}
.sidebar.mobile {
  transform: translateX(0);
}
.queue {
  position: absolute;
  bottom: 0;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 134px;
  width: 100%;
  background: rgba(#fff, 0.15);
  &-count {
    font-size: 46px;
    line-height: 44px;
    span {
      font-weight: 700;
      margin-right: 3px;
    }
  }
  p {
    font-size: 36px;
    line-height: 44px;
    margin: 0;
  }
}
.parameters {
  position: absolute;
  bottom: 27%;
  width: 100%;
  padding-left: 40px;
  &-wrap {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  &-buttons {
    background: #fff;
    border-radius: 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 50px 10px 10px;
    margin-right: 20px;
    margin-bottom: 40px;
    width: 190px;
    span {
      font-size: 48px;
      line-height: 59px;
      font-weight: 900;
    }
  }
  p {
    color: #fff;
    font-size: 36px;
    line-height: 44px;
    font-weight: 700;
  }
}
.panel {
  position: relative;
  width: 100%;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
  &-bottom {
    display: flex;
    justify-content: space-around;
    width: 100%;
    padding-bottom: 64px;
  }
  &-button {
    color: #fff;
    border: none;
    outline: none;
    border-radius: 100px;
    font-size: 28px;
    line-height: 34px;
    font-weight: 700;
    width: 280px;
    padding: 25px 0;
    &:first-child {
      background: linear-gradient(266.19deg, #8049c7 0%, #ca57fd 100%);
    }
    &:last-child {
      background: linear-gradient(
        90deg,
        #ffd748 0.02%,
        rgba(195, 199, 11, 0.96) 99.97%,
        #cac6ab 99.98%,
        #d3e9e1 99.99%
      );
    }
    &:nth-child(2) {
      background: linear-gradient(266.19deg, #169ae4 0%, #0cc4fa 100%);
    }
  }
}
.users {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  &-list {
    width: 540px;
    height: 590px;
  }
}
@media (max-width: 1320px) {
  .panel-button {
    width: 30%;
  }
  .result-store {
    left: 5%;
    bottom: 5%;
  }
}
@media (max-width: 1190px) {
  .result-content {
    width: 50%;
  }
  .sidebar {
    min-width: 35%;
  }
  .queue {
    p {
      font-size: 30px;
    }
    &-count {
      font-size: 35px;
    }
  }
  .users-list {
    width: 450px;
    height: 500px;
  }
  .card {
    width: 450px;
     height: 500px;
  }
  .parameters-buttons {
    margin-bottom: 10px;
  }
  .card-frame{
    font-size: 40px;
  }
  
}
@media (max-width: 980px) {
  .result-content {
    width: 70%;
    left: 5%;
  }
  
  .panel-button {
    font-size: 25px;
  }
  .users-list {
    width: 400px;
    height: 550px;
  }
  .card {
    width: 400px;
    height: 550px;
    p {
      line-height: 30px;
    }
  }
  .queue p {
    font-size: 25px;
  }
}
@media (max-width: 770px) {
  .sidebar {
    position: absolute;
    transform: translateX(-100%);
    z-index: 20;
  }
  .mobile-menu{
    display:block;
  }
}
@media (max-width: 560px) {
  .result-content {
    width: 90%;
    left: 5%;
  }
  .result-home {
    left: 5%;
    top: 5%;
  }
  .result-results__item {
    h3 {
      font-size: 35px;
      padding: 0;
    }
  }
  .result-results {
    padding-bottom: 30px;
  }
  .result-title {
    span {
      font-size: 25px;
    }
    h2 {
      font-size: 30px;
    }
    p {
      font-size: 16px;
    }
  }
  .result-store {
    font-size: 18px;
    width: 240px;
    bottom: 5%;
    left: 5%;
  }
  .sidebar-route {
    padding: 20px;
  }
  .parameters {
    padding: 0 10px;
  }
  .card {
    width: 80%;
    height: 70%;
  }
  .users-list {
    width: 80%;
    height: 70%;
  }
  .panel{
    &-button{
      font-size: 16px;
      padding: 5px 0;
    }
    &-bottom{
      padding-bottom: 10px;
    }
  }
  .card-wrap{
    padding: 10px;
  }
  .card-frame{
    font-size: 35px;
    top:35%;
  }
}
</style>
