<template>
  <div id="part1-documents" :class="background">
    <!-- <div v-if="page === 1" class="document1">

    </div> -->
    <div v-if="result !== ''" class="black-div"></div>
    <document class="document1" @result="sendResult" @to-end="toEnd"></document>
    <result class="result" :resultFrom="result" />
    <button class="back-btn" @click="$emit('back-to-info')">
  חזרה לפרטים
</button>
  </div>
</template>

<script>
import document from "./document.vue";
import result from "./result.vue";
export default {
  components: {
    document,
    result
  },
  data() {
    return {
      inputs: [],
      reasonAnswer: "",
      roomUser: "",
      result: "",
    };
  },
  methods: {
    sendResult(res) {
      this.result = res;
    },
    toEnd() {
      this.$emit("to-end");
    },
  },
};
</script>

<style scoped>
.document1 {
  height: 95vh;
}
.result {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
}

.black-div {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  background-color: rgba(0, 0, 0, 0.623);
  pointer-events: none;
}
.back-btn {
  font-family: "rubik";
  font-weight: bold;
  font-size: 1rem;
  background-color: #be0000;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  color: white;
  cursor: pointer;
  border: none;
  position: fixed;
  right: 1%;
  z-index: 3;
}
@media (max-width: 630px) {
  .document1 {
  height: 85vh;
} 
}
@media (max-width: 530px) {
  .document1 {
  height: 75vh;
} 
}
@media (max-width: 435px) {
  .document1 {
  height: 60vh;
  /* width: 10rem; */
} 
.back-btn {
  font-size: 0.8rem;
  top: -1rem;
}
}
@media (max-width: 360px) {
  .document1 {
  height: 53vh;
  /* width: 10rem; */
} 
}
@media (max-height: 660px) {
  .document1 {
  height: 65vh;
} 
}

</style>
