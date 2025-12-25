<template>
  <div id="part1-documents" :class="background">
    <!-- <div v-if="page === 1" class="document1">

    </div> -->
    <div v-if="result !== ''" class="black-div"></div>
    <document class="document1" @result="sendResult" @to-end="toEnd"></document>
    <result class="result" :resultFrom="result" />
    <button class="back-btn" @click="openDit = !openDit">
   פתיחת פרטים
</button>
<div v-if="openDit" class="text-div">
      <p class="text">חשוד - רב״ט לירון אסולין מ.א- 9543874 ת.ז-256333791 , מאבטח מתקנים בבא״ף 8223 
חשדות - סחר בסמים מסוכנים, שימוש והחזקה בסמים מסוכנים
בלש - סמל רוני בן משה מ.א- 8357012 בלש מצ״ח במצ״ח 6012
סימוכין - מס׳ תיק- 2025/0037 מתנהל במצ״ח יואב כאשר סימול הבסיס הינו 3</p>
      <p class="text">במצ״ח יואב התקבל דיווח המחשיד את רב״ט לירון אסולין בסחר בסמים מסוכנים, שימוש והחזקה בסמים מסוכנים מסוג ״קנאביס״ במהלך שירותו הצבאי בקרב מספר חיילים בבסיסו הממוקם בבא״ף לכיש. 
        החשוד נחקר אודות החשדות הנ״ל בתאריך 01 במרץ 2025, במהלך החקירה החשוד הסכים לביצוע בדיקת שתן, טרם כך יש להחתים אותו על טופס הסכמה על פי השלבים הבאים:</p>
      <p class="text">חלק א׳- הסכמה חופשית של החשוד על עצם נטילת דגימת השתן
חלק ב׳- נטילת דגימת השתן עצמה על פי העקרונות המוסכמים 
חלק ג׳- הצגת תוצאות הבדיקה בפני החשוד כאשר הם התקבלו חיוביות לסם מסוכן מסוג ״קנאביס״</p>
    </div>
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
      openDit: false,
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
.text-div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  background-color: #be0000;
  padding: 1rem;
  border-radius: 2rem;
}
.text {
  color: white;
  width: 20rem;
  font-family: "rubik";

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
