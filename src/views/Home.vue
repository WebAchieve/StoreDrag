<template>
  <div class="home" :style="{ backgroundImage: 'url(/img/bg.jpg' }">
    <div class="circle">
      <div class="circle-content">
        <p>Добро пожаловать в игру</p>
        <span>Пoмоги</span>
        <h1>Фармацевту</h1>
      </div>
        <div class="circle-button">
           <button @click="start()">Начать</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  methods:{
    start(){
      this.$router.push('/store')
    }
  }
};
</script>
<style lang="scss">
.home {
  height: 100%;
  position: relative;
  background-position: cover;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
}
.circle {
  width: 860px;
  height: 860px;
  background: linear-gradient(63.53deg, #2d8550 16.62%, #5e6ec2 83.38%);
  border-radius: 50%;
  position: absolute;
  left: 110px;
  top: -30px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: #fff;
  &-content{
    position: absolute;
    top:33%;
  }
  &-button{
    position: absolute;
    bottom: 20%;
  }
  p {
    font-size: 35px;
    line-height: 41px;
    letter-spacing: 0.02em;
    font-weight: 300;
    margin: 0;
    margin-bottom: 30px;
  }
  span {
    font-size: 60px;
    line-height: 66px;
    letter-spacing: 0.02em;
    font-weight: 700;
  }
  h1 {
    font-size: 80px;
    line-height: 66px;
    letter-spacing: 0.02em;
    font-weight: 700;
    margin: 0;
  }
  button {
    border: none;
    outline: none;
    color: #8e9ad5;
    font-size: 36px;
    line-height: 44px;
    font-weight: bold;
    width: 380px;
    height: 90px;
    border-radius: 100px;
  }
}
@media (max-width: 1300px){
  .circle{
    width: 600px;
    height: 600px;
    p{
      font-size: 25px;
    }
    span{
      font-size: 40px;
    }
    h1{
      font-size: 60px;
    }
    &-content{
      top:25%
    }
    &-button{
      button{
        font-size: 25px;
        width: 250px;
        height: 70px;
      }
    }
  }
}
@media (max-width: 980px){
  .circle{
    width: 500px;
    height: 500px;
    p{
      font-size: 25px;
      margin-bottom: 10px;
    }
    &-button{
        bottom: 15%;
    }
  
  }
}
@media (max-width: 760px){
  .circle{
    width: 400px;
    height: 400px;
    p{
      font-size: 18px;
      margin:0;
    }
    span{
      font-size: 25px;
    }
    h1{
      font-size: 40px;
    }
    &-button{
        bottom: 15%;
        button{
          font-size: 18px;
          width: 180px;
          height: 50px;
        }
    }
  
  }
}
@media (max-width: 560px){
  .circle{
    width: 300px;
    height: 300px;
    left:5%;
    p{
      font-size: 16px;
    }
    span{
      font-size: 20px;
      line-height: 0;
    }
    h1{
      font-size: 30px;
    }
  }
}
</style>
