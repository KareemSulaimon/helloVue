<template>
  <section id="home" > 
    
    <!--home background -->
    <div id="bg" 
     :style="{background:`url(${getImageUrl(ImageNow) })` + `no-repeat center  center/cover`}">

     >
    <div class="quote">
        <h3>{{h3Now}}</h3>
        <h1>{{h1Now}}</h1>
     </div>
    </div>
    <div class="form" >
        <h2>
          <!-- Arrow Up and Down in Home -->
        <uil-AngleUp size="30px" class="logo"  v-if="display" @click="displayArrow" />
        <uil-AngleDown size="30px" class="logo"  v-if="!display"  @click="displayArrow" />
        Request for a Service Today
        </h2>
        
        <form class="inputs" v-if="display"  action='https://formspree.io/f/xwkjkkkg' method="POST">
          <input type="text" placeholder="Your name" name="Full Name" class="item1">
          <input type="email" placeholder="Your email"  name="email" class="item2">
          <input type="tel" placeholder="Your phone" name="phone number" class="item3">
          <input type="text" name="preferred date" 
            class="item4"
            onfocus="(this.type='date')"
            onblur="(this.type='date')"
            placeholder="Date" > 
          <input type="submit" value="Get a Service" placeholder="Get a Service" class="service">
        </form>
     </div>
         
  </section>
</template>
<script>
// import {UilAngleDown, UilAngleUp } from '@iconscout/vue-unicons'
  export default {
    // components: {
    //     UilAngleDown, UilAngleUp 
    //     },
    data () {
      return {
        currentImage: 0,
        currentH1: 0,
        currentH3: 0,
        interval: '',
        display: false,
    
        images: ['city.jpg', 'house3.jpg','family.jpg'
        ],

        dataH3: [
          'We can light Everything','Keeping you Wired', 'Making Our Clients Happier'
        ],

        dataH1: [
          'Nothing is Impossible for Us',"We're the Current Specialist!"
           ,'Best  Services for Your Family'
        ],
        }
    },

 mounted() {
      this.changeImage()
      this.displayArrow()
     },

  watch: {
    display(){
      window.addEventListener('resize', this.displayArrow)
    }

    },

  methods: {
  changeImage () {
  this.interval = setInterval(() => {
  this.currentImage++
  }, 10000);
    },
  
   displayArrow() {
    if(window.innerWidth < 820) {
      this.display = this.display == true ? false : true
    }
    else if(window.innerWidth > 820) {
    this.display = this.display == true ? true : true
      }
  },
   getImageUrl(name) {
     return new URL(`../assets/images/${name}`, import.meta.url).href
      },

  },

    computed: {
      ImageNow () {
      return this.images[Math.abs(this.currentImage)% this.images.length] 
      },
      h1Now () {
      return this.dataH1[Math.abs(this.currentImage)% this.dataH1.length]
      },
      h3Now () {
      return this.dataH3[Math.abs(this.currentImage)% this.dataH3.length]
      }
      } 
}
</script>
