<template>
  <div id="information">
    <div class="container">
      <p class="text text1">
        בדף זה נתעד את פרטי העצור, פרטי העוצר, סיבת המעצר, שעת המעצר המדוייקת,
        תאריך וחתימה
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "information",
  components: {},
  data() {
    return {
    };
  },
  methods: {},
};
</script>

<style scoped>
.container {
  position: absolute;
  top: 6.5rem;
  right: -11.5rem;
  height: 15rem;
  width: 11rem;
  background-image: url("@/assets/media/information.png");
  background-size: 100% 100%;
  background-repeat: no-repeat;
  padding: 2rem;
}
.text {
  font-family: "dana";
  color: rgb(0, 0, 0);
  direction: rtl;
  font-size: 1.2rem;
  font-weight: 700;
  position: relative;
  /* top: -1rem; */
  right: -0.5rem;
}
.text1 {
  width: 12rem;
  text-align: center;
}
.text2 {
  font-size: 1.1rem;
  width: 12rem;
  position: relative;
  top: -0.5rem;
  right: -2rem;
}
.text3 {
  font-size: 1.1rem;
  width: 12rem;
  position: relative;
  top: -1.4rem;
  right: -1rem;
}
.text4 {
  width: 12rem;
  text-align: center;
  position: relative;
  top: -1.2rem;
  right: -0.5rem;
}
.text5 {
  width: 12rem;
  text-align: center;
  font-size: 1.1rem;
  position: relative;
  top: -1.3rem;
}
.text5-up {
  width: 12rem;
  text-align: center;
  font-size: 1.1rem;
  position: relative;
  top: -1.7rem;
}
.text6 {
  width: 12rem;
  text-align: center;
  font-size: 1.2rem;
  position: relative;
  top: -1.2rem;
}
</style>
