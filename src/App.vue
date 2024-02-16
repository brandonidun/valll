<template>
  <div class="page">
    <div class="header">Val's Day <span>by Brandon</span></div>

    <div class="vals">
      <div class="happy">happy</div>
      <img class="balloon" src="/Balloon2.png" alt="" /> Valentine's Day
      <img class="calendar" src="/Calendar2.png" alt="" />
    </div>
    <br />
    <div class="if">LIZA AIKINS</div>
    <div class="tour">
      <button @click="startTour()">Click Me to Start Tour</button>
    </div>
    <div>
      <audio id="mySong" src="/song.mp3" type="audio/mp3"></audio>
    </div>
    <div class="first-section">
      <div class="img1"><img src="/Cupcake.png" alt="" /></div>
      <div class="card">
        <div class="if">6velvet cupcakes</div>
        <br />
        only say how much i <br />
        care about you
      </div>
    </div>
    <div class="first-section">
      <div class="card">
        "cheers to more <br />
        <div class="if">
          'if he wanted to <br />
          he will' <br />
        </div>
        moments with you"
      </div>
      <div class="img1"><img src="/glasses2.png" alt="" /></div>
    </div>
    <div class="first-section">
      <div class="img1"><img src="/arrow.png" alt="" /></div>
      <div class="card">
        "I know you're trouble but i dont mind<br />
        <div class="if">
          'Wasting <br />
          Eyes' <br />
        </div>
        on you"
      </div>
    </div>
    <div class="first-section">
      <div class="card">
        "so, <br />
        <div class="if">chocalatey girl</div>
        <br />
        from Ghana"
      </div>
      <div class="img1"><img src="/Chocolate2.png" alt="" /></div>
    </div>
    <div class="answer">
      would you have been my valentine?
      <div>
        <button @click="onYesClick()">YES😂</button>
        <button @click="onNoClick()">no😔</button>
      </div>
      <div v-if="showYes" class="yes">
        <a href="https://maps.app.goo.gl/hLWRm2vjLtWgKu5x9">Location</a>
        next weekend?
      </div>
      <div v-if="showNo" class="no">you deserve big aah bracelets</div>
      <div class="stop" id="tourTarget"></div>
    </div>
    <!-- <div class="img">
      <img src="/magnet.png" alt="" />
      <img src="/glasses.png" alt="" />
      <img src="/arrow.png" alt="" />
      <img src="/Chocolate.png" alt="" />
    </div> -->
  </div>
</template>


<script>
// import emailjs from "emailjs-com";

export default {
  data() {
    return {
      showYes: false, // Controls visibility of "yes" content
      showNo: false, // Controls visibility of "no" content
    };
  },

  methods: {
    onYesClick() {
      this.showYes = true;
      this.showNo = false; // Ensure "no" content is hidden when "yes" is clicked
    },
    onNoClick() {
      this.showNo = true;
      this.showYes = false; // Ensure "yes" content is hidden when "no" is clicked
    },
    loadGsapAndStart() {
      // Load GSAP main library
      const gsapScript = document.createElement("script");
      gsapScript.src =
        "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.10.4/gsap.min.js";
      gsapScript.onload = () => {
        // Once GSAP is loaded, load ScrollToPlugin
        const scrollToPluginScript = document.createElement("script");
        scrollToPluginScript.src =
          "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.10.4/ScrollToPlugin.min.js";
        scrollToPluginScript.onload = () => {
          // Now that GSAP and ScrollToPlugin are loaded, start the tour
          this.startTour();
        };
        document.head.appendChild(scrollToPluginScript);
      };
      document.head.appendChild(gsapScript);
    },
    startTour() {
      // Ensure GSAP globals are available in this scope
      const gsap = window.gsap;
      gsap.registerPlugin(window.ScrollToPlugin);

      // Your GSAP code here, for example:
      gsap.to(window, { duration: 20, scrollTo: "#tourTarget" });

      // Optionally, play audio
      const song = document.getElementById("mySong");
      if (song) {
        song.play();
      }
    },
    // sendEmail() {
    //   // Initialize EmailJS with your userID
    //   emailjs.init("user_XXXXX");

    //   let templateParams = {
    //     // Your template params structure, e.g.,
    //     to_name: "Liza",
    //     from_name: "Brandon",
    //     message: "Happy Valentine's Day! Would you be my Valentine?",
    //     // Add other parameters as needed according to your template
    //   };

    //   emailjs.send("your_service_id", "your_template_id", templateParams).then(
    //     function (response) {
    //       console.log("SUCCESS!", response.status, response.text);
    //     },
    //     function (error) {
    //       console.log("FAILED...", error);
    //     }
    //   );
    // },
  },
};
</script>

<style>
#app {
  font-family: "Playfair Display", serif;
  padding: 0 50px 0 30px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* color: rgb(229, 57, 54); */
  color: #e91e63;
}

.page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.header {
  width: 100%;
  border-bottom: 2px solid #e91e63;
  font-family: "Playfair Display", serif;
  font-size: 30px;
  font-weight: 500;
  font-style: italic;
  text-align: left;
  padding: 15px;
}

.header span {
  font-size: 15px;
  font-weight: 300;
  font-style: normal;
}

.img1 img {
  max-height: 50vh;
  margin: 0 50px 0 50px;
}

.card {
  margin: 0 50px 0 50px;
}

.card p {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Playfair Display", serif;
  font-size: 60px;
  line-height: 2;
  font-weight: 500;
  padding: 20px;
  min-width: 80%;
  min-height: 60vh;
  text-align: center;
  background: rgba(255, 255, 255, 0.183);
  border-radius: 30px;
  max-width: 40%;
}

.if {
  font-size: 40px;
  font-weight: 300;
  font-style: italic;
  color: black;
}

.img {
  display: flex;
  justify-content: center;
  margin-top: 20vh;
}
.img img {
  width: 15%;
  height: 15%;
}
.happy {
  font-size: 90px;
}

.vals {
  font-family: "Playfair Display", serif;
  font-size: 120px;
  font-weight: 700;
  margin-top: 20vh;
  position: relative;
}

.balloon {
  width: 9%;
  position: absolute;
  top: -7%;
  left: -5%;
}

.calendar {
  width: 9%;
  position: absolute;
  bottom: -8%;
  right: -5%;
}

.name {
  font-family: "Playfair Display", serif;
  font-size: 45px;
  font-weight: 500;
  font-style: italic;
}

.tour button {
  margin-top: 5vh;
  padding: 10px;
  font-family: "Playfair Display", serif;
  background-color: transparent;
  border: 1px solid #e91e63;
}

.tour button:hover {
  background-color: #e91e63;
  color: white;
  cursor: pointer;
}

button {
  margin-top: 5vh;
  padding: 20px 40px 20px 40px;
  margin: 30px;
  font-family: "Playfair Display", serif;
  background-color: transparent;
  border: 1px solid #e91e63;
}

button:hover {
  background-color: #e91e63;
  color: white;
  cursor: pointer;
}

.first-section {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  margin-top: 20vh;
}

.answer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: "Playfair Display", serif;
  font-size: 45px;
  font-weight: 500;
  font-style: italic;
  margin-top: 30vh;
  margin-bottom: 30vh;
  background-color: rgba(255, 255, 255, 0.151);
  padding: 200px;
  border-radius: 30px;
  position: relative;
}
.stop {
  position: absolute;
  top: -140px;
  left: 0;
}

.yes {
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  color: black;
  margin-top: 20px;
}

.no {
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  color: black;
  margin-top: 20px;
}
/* html {
  scroll-behavior: smooth;
} */
</style>
