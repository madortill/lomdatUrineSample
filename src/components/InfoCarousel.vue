<template>
  <div :class="carouselClass">
    <div class="carousel" data-bs-theme="dark">
      <div class="inside-container">
        <!-- חץ אחורה -->
        <div class="carousel-control-prev" type="button" @click="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        </div>

        <!-- סליידים -->
        <div class="carousel-inner">
          <div
            v-for="(slide, index) in info"
            :key="index"
            class="carousel-item"
            :class="{ active: index === activeIndex }"
          >
            <div class="carousel-caption">
              <div class="info-text">
                {{ slide }}
              </div>
            </div>
          </div>
        </div>

        <!-- חץ קדימה -->
        <div class="carousel-control-next" type="button" @click="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
        </div>
      </div>

      <!-- אינדיקטורים (נקודות) -->
      <div class="carousel-indicators">
        <p
          v-for="(slide, index) in info"
          :key="index"
          :class="{ active: index === activeIndex }"
          @click="handleSelect(index)"
        ></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "info-carousel",
  props: ["activeIndex"],
  emits: ["update:activeIndex"],
  data() {
    return {
      emits: ["update:activeIndex", "length"],
      info: [
        'חשוד – רב\"ט לירון אסולין מ.א - 9543874 ת.ז- 256333791, מאבטח מתקנים בבא"ף 8223\n\
חשדות – סחר בסמים מסוכנים, שימוש והחזקה בסמים מסוכנים\n\
בלש – סמל רוני בן משה מ.א - 8357012 בלש מצ״ח במצ\"ח 6012\n\
סימוכין – תיק מספר 2025/0037 מתנהל במצ\"ח יואב, כאשר סימול הבסיס הינו 3',
        'במצ״ח יואב התקבל דיווח המחשיד את רב״ט לירון אסולין בסחר בסמים מסוכנים, שימוש והחזקה בסמים מסוכנים מסוג ״קנאביס״ במהלך שירותו הצבאי בקרב מספר חיילים בבסיסו הממוקם בבא״ף לכיש.\n\
החשוד נחקר אודות החשדות הנ״ל בתאריך 01 במרץ 2025, במהלך החקירה החשוד הסכים לביצוע בדיקת שתן, טרם כך יש להחתים אותו על טופס הסכמה על פי השלבים הבאים...',
        'חלק א׳- הסכמה חופשית של החשוד על עצם נטילת דגימת השתן\n\
חלק ב׳- נטילת דגימת השתן עצמה על פי העקרונות המוסכמים\n\
חלק ג׳- הצגת תוצאות הבדיקה בפני החשוד כאשר הם התקבלו חיוביות לסם מסוכן מסוג ״קנאביס״',
      ],
    };
  },
  mounted() {
  this.$emit("length", this.info.length);
},
  computed: {
    isFirst() {
      return this.activeIndex === 0;
    },
    isLast() {
      return this.activeIndex === this.info.length - 1;
    },
    carouselClass() {
      return `
        custom-carousel
        ${this.isFirst ? "hide-prev" : ""}
        ${this.isLast ? "hide-next" : ""}
      `.trim();
    },
  },
  methods: {
    handleSelect(selectedIndex) {
      this.$emit("update:activeIndex", selectedIndex);
    },
    next() {
      if (!this.isLast) {
        this.$emit("update:activeIndex", this.activeIndex + 1);
      }
    },
    prev() {
      if (!this.isFirst) {
        this.$emit("update:activeIndex", this.activeIndex - 1);
      }
    },
  },
};
</script>

<style scoped>
.inside-container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-family: "rubik";
}

/* ===========================
   📐 GENERAL LAYOUT
=========================== */
.carousel-inner {
  direction: rtl;
  width: 100%;
  height: 100%;
  position: relative;
}

.carousel-item {
  text-align: right;
  color: white;
  height: 25rem;
  background: transparent;
  display: none;
  justify-content: center;
  align-items: center;
}

.carousel-item.active {
  display: flex;
}

.carousel {
  border: 6px solid #5d76da;
  border-radius: 0.6rem;
  overflow: hidden;
  width: 40rem;
  margin: 0 auto;
  height: 25rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  animation: float 3s ease-in-out infinite;
  justify-content: space-between;
  background-color: #5d76da;
  color: white;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

/* ===========================
   🔄 ARROW POSITIONS
=========================== */
.carousel-control-prev {
  right: 0;
  left: auto;
  cursor: pointer;
}

.carousel-control-next {
  left: 0;
  right: auto;
  cursor: pointer;
}

/* ===========================
   ➤ CUSTOM ARROWS
=========================== */
.custom-carousel .carousel-control-prev,
.custom-carousel .carousel-control-next {
  background: none !important;
  opacity: 1 !important;
}

.custom-carousel .carousel-control-prev-icon,
.custom-carousel .carousel-control-next-icon {
  background-image: none !important;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.custom-carousel .carousel-control-prev-icon::after,
.custom-carousel .carousel-control-next-icon::after {
  content: "";
  display: block;
  width: 16px;
  height: 16px;
  border-top: 3px solid #ffffff;
  border-right: 3px solid #ffffff;
  transition: transform 0.2s ease;
}

.custom-carousel .carousel-control-prev-icon::after {
  transform: rotate(45deg);
}

.custom-carousel .carousel-control-next-icon::after {
  transform: rotate(225deg);
}

/* ===========================
   ❌ HIDE ARROWS AT ENDS
=========================== */
.custom-carousel.hide-prev .carousel-control-prev,
.custom-carousel.hide-next .carousel-control-next {
  opacity: 0 !important;
  pointer-events: none !important;
  visibility: hidden !important;
}

/* ===========================
   ⚪ DOT INDICATORS — FIXED VERSION
=========================== */
.carousel-indicators {
  bottom: 1rem;
    display: flex;
    justify-content: center;
    position: absolute;
}

.carousel-indicators p {
  display: inline-block;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #5e1928 ;
  transition: all 0.3s ease;
  margin: 0 6px;
  cursor: pointer;
}

.carousel-indicators p.active {
  background-color: rgb(192, 78, 78);
  width: 14px;
  height: 14px;
}

/* ===========================
   🧾 TEXT STYLING
=========================== */
.info-text {
  color: white;
  font-size: 1.15rem;
  margin: 0;
  direction: rtl;
  white-space: pre-wrap;
  line-height: 1.8;
  max-width: 80%;
  display: flex;
  height: 80%;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.carousel-caption {
  position: static;
  width: 90%;
  text-align: right;
  padding: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

@media (max-width: 610px) {
  .carousel {
    width: 33rem;
    height: 35rem;
  }
  .info-text {
  margin-top: 6rem;
  max-width: 100%;
}
}
@media (max-width: 440px) {
  .carousel {
    width: 27rem;
    height: 37rem;
  }
  .info-text {
  margin-top: 8rem;
  max-width: 100%;
}

}
</style>
