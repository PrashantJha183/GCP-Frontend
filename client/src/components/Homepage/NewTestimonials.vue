<template>
  <div>
    <section class="sectioon_container">
      <div class="testimonial-header">
        <h2>TESTIMONIAL</h2>
        <h1 class="fw-bold">Customer is Our Top<br />Priority</h1>
        <p>
          We survey all of our clients, the results of which go directly<br />to
          our CEO.
        </p>
      </div>

      <!-- Testimonial Slider -->
      <div class="testimonial-slider">
        <button class="slider-btn left-btn" @click="goPrev">&lt;</button>

        <div class="card_main">
          <div
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="container_card"
            :style="{
              transform: `translateX(-${currentIndex * 100}%)`,
              transition: 'transform 0.5s ease',
            }"
          >
            <!-- @mouseenter="stopAutoSlide" -->
            <div class="container_card_content">
              <img
                :src="testimonial.companyLogo"
                alt="Company Logo"
                class="company-logo"
              />
              <h4 style="font-weight: bold">{{ testimonial.title }}</h4>
              <p style="text-align: justify">{{ testimonial.description }}</p>
              <h4 style="font-weight: bold">{{ testimonial.name }}</h4>
              <p class="position">{{ testimonial.position }}</p>
            </div>
            <div class="container_card_pofilephoto">
              <img :src="testimonial.profileImage" class="profile-img" />
            </div>
          </div>
        </div>

        <button class="slider-btn right-btn" @click="goNext">&gt;</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      testimonials: [
        {
          // companyLogo: require('@/assets/homepage/Brand/testimonial/CompanyLogo.png'),
          companyLogo: require("@/assets/homepage/testimonial/CompanyLogo.png"),

          description:
            "As a client of Grip Chain Packtech, we have been thoroughly impressed with their exceptional service and high-quality packaging solutions. Their products have significantly enhanced our operational efficiency, and their team’s dedication to customer satisfaction is truly commendable. We highly value our partnership with Grip Chain Packtech and look forward to continued success together.",
          name: "Mr. Arnav Bajaj",
          position: "Business Developer at Amrit Food",
          profileImage: require("@/assets/homepage/testimonial/Arnav_bajaj.jpg"),
        },
        {
          companyLogo: require("@/assets/homepage/testimonial/CompanyLogo.png"),

          description:
            "As the Director of Shakuntala Industries, we’ve had the pleasure of working with Grip Chain Packtech, and their packaging solutions have been pivotal in enhancing the efficiency of our operations. Their commitment to quality and customer satisfaction is outstanding, and we truly appreciate their professional approach. We look forward to a continued and successful partnership with Grip Chain Packtech.",
          name: "Mr. Rahul Chaudhary",
          position: "Director at Shakuntala Industries",
          profileImage: require("@/assets/homepage/testimonial/testimonial_2.jpg"),
        },
        {
          companyLogo: require("@/assets/homepage/testimonial/CompanyLogo.png"),

          description:
            "Working with Grip Chain Packtech has been a fantastic experience for us at Ruma Natural LLP. Their dedication to delivering high-quality packaging solutions has greatly enhanced our product presentation and ensured the safe delivery of our goods. Their team is highly reliable and customer-focused, and we are proud to be their clients. We look forward to a long-lasting collaboration.",
          name: "Mr. Rakesh Aggarwal",
          position: "Vice Chairperson at Ruma Natural LLP",
          profileImage: require("@/assets/homepage/testimonial/testimonial_3.jpg"),
        },
      ],
      currentIndex: 0,
    };
  },
  mounted() {
    // Start the auto-slide when the component is mounted
    this.startAutoSlide();
  },
  methods: {
    goPrev() {
      this.currentIndex =
        (this.currentIndex - 1 + this.testimonials.length) %
        this.testimonials.length;
      this.restartAutoSlide();
    },
    goNext() {
      this.currentIndex = (this.currentIndex + 1) % this.testimonials.length;
      this.restartAutoSlide();
    },
    startAutoSlide() {
      // Automatically move to the next slide every 3 seconds
      this.autoSlideInterval = setInterval(() => {
        this.goNext();
      }, 3000);
    },
    stopAutoSlide() {
      // Stop the auto-slide
      if (this.autoSlideInterval) {
        clearInterval(this.autoSlideInterval);
        this.autoSlideInterval = null;
        this.autoSlideInterval = null;
      }
    },
    restartAutoSlide() {
      // Stop and restart the auto-slide
      this.stopAutoSlide();
      this.startAutoSlide();
    },
  },
  beforeDestroy() {
    // Clean up the interval when the component is destroyed
    this.stopAutoSlide();
  },
};
</script>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css");
/* body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
} */

.sectioon_container {
  text-align: center;
  padding: 20px;
}

.testimonial-header h2 {
  font-size: 16px;
  color: #777;
  margin-bottom: 5px;
  text-transform: uppercase;
}

.testimonial-header h1 {
  font-size: 32px;
  color: #000;
  font-weight: bold;
  margin: 15px 0;
}

.testimonial-header p {
  font-size: 14px;
  color: #333;
  margin-bottom: 30px;
}

.testimonial-slider {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.slider-btn {
  background: white;
  border: none;
  font-size: 30px;
  color: black;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  /* font-weight: bold; */
}
.right-btn {
  font-weight: bold;
}

.left-btn {
  font-weight: bold;
}

.slider-btn:hover {
  background: #f9f9f9;
  /* color: #fff; */
}

.card_main {
  display: flex;
  transition: transform 0.5s ease-in-out;
  width: 100%;
  overflow: hidden;
  height: auto;
  border-radius: 20px;
  background-color: #f9f9f9;
  /* background-color: cadetblue; */
  border-radius: 30px;
}

.container_card {
  /* background-color: #f9f9f9; */
  flex: 0 0 100%;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  /* width: 100%; */
  border-radius: 10px;
  /* box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); */
  margin-bottom: 20px;
  margin-top: 20px;
  /* margin: 30px; */
}

.container_card_content {
  width: 60%;
  padding: 20px;
  box-sizing: border-box;
  text-align: left;
  /* background-color: aqua; */
  /* border-radius: 18px; */
}

.company-logo {
  width: 80px;
  margin-bottom: 15px;
}

.container_card_pofilephoto {
  width: 40%;
  /* height: 100%; */
  /* padding: 20px; */
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  /* background-color: yellow; */
  border-radius: 18px;
}

.profile-img {
  width: 320px;
  height: 320px;
  object-fit: cover;
  border-radius: 50%;
  /* margin: 10px; */
  /* border: 2px solid #ddd; */
  /* margin-right: 50px; */
  padding: 10px;
}

@media screen and (max-width: 768px) {
  .testimonial-header h1 {
    font-size: 24px;
  }

  .container_card_content {
    padding: 15px;
    /* text-align: justify; */
  }

  .profile-img {
    width: 200px;
    height: 200px;
    /* margin-left: 50px; */
  }

  .slider-btn {
    width: 30px;
    height: 30px;
    font-size: 25px;
    font-weight: bold;
  }
}

@media screen and (max-width: 480px) {
  .testimonial-header h1 {
    font-size: 20px;
  }

  .testimonial-slider {
    width: 100%;
  }
  .card_main {
    width: 100%;
  }
  .container_card {
    flex-direction: column;
    align-items: center;
    text-align: center;
    width: 100%;
  }

  .container_card_content {
    width: 100%;
    padding: 10px;
  }

  .container_card_pofilephoto {
    /* margin-top: 10px; */
    /* height: 40%; */
    width: 100%;
  }

  .profile-img {
    width: 210px;
    height: 200px;
    margin: 8px;
  }

  .slider-btn {
    width: 25px;
    height: 25px;
    font-size: 20px;
    font-weight: bold;
  }
}
</style>
