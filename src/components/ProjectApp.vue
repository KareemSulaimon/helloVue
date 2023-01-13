<template>
  <section id="project">
    <a href="#" class="luqtech-facebook">@luqtech engineering</a>
    <h1>Our Projects</h1>
    <div class="heading">
      <h3 v-for="(item, index) in list" :key="index" 
      @click="logout(index)"
      :class="Index == index ? 'border' : '' ">{{item}}</h3>
    </div>
    <div v-for="(item, index) in gallery" :key="item" class="gallery">
      <div v-if="Index == index">
        <img v-for="obj in item.pictures" :key="obj" :src=" getImageUrl(obj)">
      </div> 
    </div>
    <small>view all projects<uil-arrowRight size="20px" class="logo" /></small>
  

  <div id="testimonial">
    <div class="testimonialHead">
      <div  class="our-statisticsFirst">
        <h3>Our Statistics</h3>
        <h1>Some Important Facts</h1>
      </div>
      <div class="projectType">
        <div v-for="project in tyoeofProject" :key="project">
          <h1>{{project.header}}</h1>
          <h3>{{project.project }}</h3>
        </div>
      </div>
   </div>
    <div class="testimonies">
     <div class="overall-testimonies">
        <div  v-for="(head, index) in Testimonial" :key="index"  class="testimonial">
          <Transition name="testimonial-fade">
              <div v-if="currentSlide == index" :class="head" class="testimonials" >
                <div class="header">
                  <span class="clientImg">

      <!-- client Imagges Here -->
                      <img :key="img" :src=" getImageUrl(head.image)" alt="client image">
                  </span> 
                  <div class="clients-header">
                      <h3>What Our Clients Say</h3>
                      <h1>{{head.header}}</h1>
                  </div>
                  </div>
                  <p>{{head.paragraph}}</p>
                    <h5> - {{ head.client}}</h5>
                  </div>
            </Transition>
          </div> 

        <div class="indicator">
        <div @click="makeActive(index)"
            v-for="(head, index) in Testimonial" 
              :key="index" 
            :style="currentSlide == index ? {background: 'blue'} : {background: 'white'}">
                
          </div>
          </div>
        </div>

        <div class="emergencyLine">
            <div class="emergency">
              <header>Emergency Service</header>
              <h3>If this is an emergency outside of normal business hours, call us</h3> 
              <a href="tel:+2349079119413"> 
              <uil-phoneAlt size="20px"  /><h2>+2349079119413</h2></a>  
            </div>
              <span class="projectImg">
              <img  src='../assets/images/ab.jpg'>
              </span>
          </div>
    </div>


 </div>

   </section> 

</template>

<script>
// import { UilPhoneAlt, } from '@iconscout/vue-unicons'

export default {
// components: {UilPhoneAlt,},
  
 data() {
    return {
currentSlide: 1,
Index: 0,
interval: "",

tyoeofProject: [
{header: '5000+', project: 'Residential Projects' },
{header: '1500+', project: 'Commercial Projects' },
{header: '100+', project: 'Industrial Projects' },
],

Testimonial: [
  { header:'Professional, Reliable & Cost Effective', paragraph:`"We've been using your company and from the very beginning found him and 
  his team to be extremely professional and Knowledgeable.We wouldn't have any hesitation in recommending their services"`,
  client: 'Mr Charles', image:'client1.jpg' },
  { header:'Professional, Reliable & Cost Effective', paragraph:`"We've been using your company and from the very beginning found him and 
  his team to be extremely professional and Knowledgeable.We wouldn't have any hesitation in recommending their services"`,
  client: 'Mr ola', image: 'client2.jpg'},
  { header:'Professional, Reliable & Cost Effective', paragraph:`"We've been using your company and from the very beginning found him and 
  his team to be extremely professional and Knowledgeable.We wouldn't have any hesitation in recommending their services"`,
  client: 'Mr obi', image: 'client3.jpg'},
  ],

gallery:[
  { pictures:[
  'gallery1.jpg' ,'gallery2.jpg',
 'gallery3.jpg','gallery 4.jpg',
 'gallery5.jpg' ,'gallery6.jpg',
 'gallery8.jpg','gallery7.jpg'
    ] } ,
  { pictures:[
   'gallery1.jpg','gallery2.jpg',
 'gallery3.jpg','gallery 4.jpg'
    ]},
  {  pictures:[
   'gallery8.jpg','gallery7.jpg' 

 ]}
     ],
list: ['Residential', 'Commercial', 'Industrial'],

    }
 },
 mounted() {
 this.interval = setInterval(() => {
  this.currentSlide = this.currentSlide == 2 ? 0 : this.currentSlide + 1
  }, 4000);
 },
 beforeUnmount() {
  clearInterval(this.interval)
 },

 methods: {
  makeActive(index) {
  this.currentSlide = index;  
  },

 logout(index) {
this.Index = index;
},
 getImageUrl(name) {
     return new URL(`../assets/images/${name}`, import.meta.url).href
      },


   } 

}
</script>

<style lang='scss'>
.testimonial-fade-enter-active,
 .testimonial-fade-leave-active {
  transition: all 1s ease;
}

.testimonial-fade-enter-from,
 .testimonial-fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
.testimonial-fade-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}

</style>