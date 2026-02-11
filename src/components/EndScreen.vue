<template>
  <div id="end-screen">
    <div class="end-container">
      <p class="endText"> {{ userName }} סיימת למלא את המסמך בהצלחה! </p>
      <p class="endText">כל הכבוד!</p>
      <button class="againBtn" @click="startAgain">לתחילת הלומדה</button>
      <!-- <img src="../assets/media/endScreen/confety.gif" alt="confety" class="confety"> -->
    </div>
    <about></about>
  </div>
</template>

<script>
import About from "@/components/About.vue";
export default {
  name: "end-screen",
  props: ['userName'],
  components: {
    About
  },
  mounted() {
    this.launchConfetti();
  },
  methods: {
    startAgain() {
      this.$emit("start-over");
      
    },
    launchConfetti() {
  const colors = ["#0057FF", "#FF1E1E"];
  const pieces = 200;
  const container = document.body;
  const screenWidth = window.innerWidth;
  const screenHeight = window.innerHeight;

  for (let i = 0; i < pieces; i++) {
    const confetti = document.createElement("div");
    confetti.classList.add("confetti-piece");

    // התחלה מלמטה
    confetti.style.left = screenWidth / 2 + "px";
    confetti.style.bottom = "0px";

    // צבע וגודל אקראי
    const size = 8 + Math.random() * 12;
    confetti.style.width = size + "px";
    confetti.style.height = size * 1.4 + "px";
    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];

    // פיזור אקראי
    const x = (Math.random() - 0.5) * screenWidth; // צדדים
    const y = screenHeight * (0.5 + Math.random() * 0.5); // למעלה

    // אנימציה
    const duration = 1 + Math.random() * 1 + "s";
    confetti.style.transition = `transform ${duration} ease-out, opacity ${duration} ease-out`;

    container.appendChild(confetti);

    // נותנים למשהו זמן להיכנס ל-DOM ואז מזיזים
    setTimeout(() => {
      confetti.style.transform = `translate(${x}px, -${y}px) rotate(${360 + Math.random() * 360}deg)`;
      confetti.style.opacity = 0;
    }, 50);

    setTimeout(() => confetti.remove(), 3000);
  }
},
  },
};
</script>

<style>
#end-screen {
  background-image: url("@/assets/media/endScreen/end.png");
  background-size: cover;
  width: 100vw;
  height: 100vh;
  background-position: center;
  background-repeat: no-repeat;
  overflow: hidden;
  position: relative;
}
.graphic {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  position: relative;
}

.car-container {
  position: absolute;
  top: 3rem; /* שימי לב למיקום מעל הכביש */
  left: 100%; /* מתחילה מחוץ למסך מימין */
  width: 35rem;
  animation: drive 10s linear forwards; /* האנימציה */
  z-index: 3;
}

@keyframes drive {
  0% {
    left: 100%;
  }
  100% {
    left: -40rem; /* יוצאת שמאלה מחוץ למסך */
  }
}

.policeCar {
  width: 100%;
}

.road {
  width: 100rem;
  height: 5rem;
  position: relative;
  z-index: 2;
  margin-top: 10rem;
}
.end-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 6rem;
  padding: 2rem;
}
.endText {
  font-family: "rubik";
  font-size: 2rem;
  margin: 0.3rem;
  color: white;
  font-family: "abraham";
  text-align: center;

}
.againBtn {
  font-family: "rubik";
  font-weight: bold;
  font-size: 1.5rem;
  background-color: #be0000;
  padding: 1rem 2rem;
  border-radius: 1rem;
  color: white;
  cursor: pointer;
  border: none;
  margin-top: 3rem;
}
.againBtn:hover {
  background-color: #940000;
}
.againBtn:active {
  background-color: #d40000;
}
.confetti-piece {
  position: fixed;
  bottom: 0;
  left: 0; /* נקבע ב-JS */
  border-radius: 2px;
  pointer-events: none;
  opacity: 1;
  /* אין keyframes */
}

@keyframes popUp {
  0% {
    transform: translate(0, 0) rotate(0deg);
    opacity: 1;
  }
  100% {
    transform: translate(var(--x), -var(--y)) rotate(720deg);
    opacity: 0;
  }
}
</style>
