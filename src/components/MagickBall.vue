<template>
  <div class="ball">
    <div class="ball__wrapper">
      <div class="ball__body">
        <div class="ball__prediction">
          {{ text }}
        </div>
        <div class="ball__animation">
          <div class="spinner big" v-bind:class="{ active: isActive }"></div>
          <div
            class="spinner semi-big"
            v-bind:class="{ active: isActive }"
          ></div>
          <div class="spinner medium" v-bind:class="{ active: isActive }"></div>
          <div
            class="spinner semi-small"
            v-bind:class="{ active: isActive }"
          ></div>
        </div>
      </div>
      <div class="btn" @click="prediction">
        Получить <br />
        предсказание
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  data() {
    return {
      text: "",
      isActive: true,
    };
  },
  methods: {
    ...mapMutations(["ADDTODOCATEGORY"]),
    prediction() {
      this.isActive = false;

      setTimeout(() => {
        this.text = "Ты станешь геем";
        this.isActive = true;
      }, 2500);
      
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.ball
  &__wrapper
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
  &__body
    height: 400px
    width: 400px
    border-radius: 50%
    position: relative
    display: flex
    align-items: center
    justify-content: center
  &__animation
    position: absolute
    height: 100%
    width: 100%
    left: -50%
    top: 0
  &__prediction
    font-size: 18px

.btn
  margin: 20px
  background-color: #4577D4
  height: 50px
  display: flex
  align-items: center
  justify-content: center
  color: #fff
  font-size: 18px
  padding: 5px 15px
  border-radius: 5px
  cursor: pointer

.big
  width: calc(50% - 10px)
  height: calc(100% - 20px)
  border: 10px solid #0aa
  top: 0
  animation: ring1 4s linear infinite

.semi-big
  width: calc(42.5% - 10px)
  height: calc(85% - 20px)
  border: 10px solid #9F3ED5
  top: 7.5%
  animation: ring2 3s linear infinite

.medium
  width: calc(35% - 10px)
  height: calc(70% - 20px)
  border: 10px solid #CD0074
  top: 15%
  animation: ring1 5s linear infinite

.semi-small
  width: calc(27.5% - 10px)
  height: calc(55% - 20px)
  border: 10px solid #9FEE00
  top: 22.5%
  animation: ring1 2s linear infinite

.spinner
  border-radius: 300px 0 0 300px
  z-index: 200
  border-right: none
  transform-origin: right center
  position: absolute
  right: 0
  &:after
    display: block
    content: ""
    border-radius: 300px 0 0 0
    position: absolute
    left: -11px
    top: -11px
    height: 50%
    width: 100%
    border-top: 12px solid #fff
    border-left: 12px solid #fff

.active
  animation-play-state: paused

@keyframes ring1
  0%
    transform: rotate(0deg)
  100%
    transform: rotate(360deg)

@keyframes ring2
  0%
    transform: rotate(0deg)
  50%
    transform: rotate(-180deg)
  100%
    transform: rotate(-360deg)
</style>

