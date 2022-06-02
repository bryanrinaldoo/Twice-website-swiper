<template>
  <div class="containerPage">
    
    <div ref="swiper" class="swiper">

      <div class="swiper-wrapper ">

        <!-- Slides 1 -->
        <div class="swiper-slide bgColor1 menu1">
          <img class="w-full mb-4 mt-4 logoMenu" src="../assets/logo.png">
          <div class="mx-9">
            <h3 class="text-left">Twice</h3>
            <p class="text-justify">
                is a South Korean girl group formed by JYP Entertainment. The group is composed of nine members.
                    Twice was formed under the television program Sixteen and debuted on October 20, 2015, with the
                    extended play The Story Begins.</p>
          </div>
        </div>

        <!-- slide choose -->
        <div class="swiper-slide">

          <div class="content choose" style="height:746px;">

            <div class="content">
              <div class="backgroundChooseSection background choose1Pic">
                <p class="text-2xl" v-on:click="chooseMember">Members</p>
              </div>
              
            </div>

            <div class="content">
              <div class="backgroundChooseSection background choose2Pic">
                <p class="text-2xl" v-on:click="chooseAlbum">Albums</p>
              </div>

            </div>

          </div>

        </div>

        <!-- Slides Members -->
        <div class="swiper-slide" v-for="(i,key) in member" :key="key">
          <div class="buttonSection">
            <a :href="i.vlog" class="buttonMore" :style="{'background-color': i.colour}" target="_blank" rel="noopener noreferrer">
              <span class="icon">❤️</span>
              <span class="text">Want to know more!</span>
            </a>
          </div>

          <div class="content" style="height:746px;">
            
            <div class="backgroundSection zoom_animation background" :class="i.background"></div>


            <div class="nameSection">
              <p class="text-2xl">{{i.emoji}}</p>
              <h2 class="animateText">{{i.name}}</h2>
              <p>{{i.birthday}}</p>
            </div>

          </div>

        </div>

        <!-- Slides Albums -->
        <div class="swiper-slide bgColor2">

          <div ref="swiperAlbum" class="swiperAlbum">

            <div class="swiper-wrapper ">

              <div class="swiper-slide album bgColor2" v-for="(j,key) in albums" :key="key">
              <div class="buttonSectionAlbum">
                <div class="buttonMore albumBtn">
                  <span class="icon">🎥</span>
                  <span class="text">Click Image!</span>
                </div>
              </div>
                <a :href="j.url" target="_blank" rel="noopener noreferrer"><img class=" mb-4 mt-4" :src="j.image"></a>
                <div class="px-6">
                  <div class="font-bold text-xl mb-2">{{j.name}}</div>
                </div>
              </div>
            </div>

            <div class="swiper-pagination-album"></div>

            <div class="swiper-button-prev mx-4"></div>
            <div class="swiper-button-next mx-4"></div>
          </div>

        </div>
        
        <!-- slide compare  -->
        <!-- <div class="swiper-slide ">
          <div class="content" style="height:746px;">
            <div class="compareContent">
              
              <TwentyTwenty
              before= "https://interaktif.kompas.id/wp-content/uploads/sites/316/2019/06/01_before.jpg"
                after= "https://interaktif.kompas.id/wp-content/uploads/sites/316/2019/06/01_after.jpg"
         
                beforeLabel="BEFORE"
                afterLabel="AFTER" />
            </div>
          </div>
        </div> -->

        <!-- slide profile -->
        <div class="swiper-slide bgColor1 menu1">
          <img class="w-full mb-4 mt-4 profilePic" src="../assets/profile.png">
          <div class="mx-9">
            <h3 class="text-left">Bryan Rinaldo</h3>
            <div class="socmed" v-for="(k,key) in socmed" :key="key">
              <a :href="k.url" class="icon" :class="k.class" target="_blank"
                  rel="noopener noreferrer">
                  <div class="tooltip">{{k.name}}</div>
                  <span><i :class="k.icon"></i></span>
              </a>
            </div>

          </div>
        </div>

      </div>

      <!-- If we need pagination -->
      <div class="swiper-pagination"></div>

    </div>
  </div>
</template>

<script>

import Swiper, { Navigation, Pagination, EffectFade, Mousewheel} from 'swiper'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import 'swiper/css/effect-fade'
import 'swiper/css/mousewheel'

// import 'vue-twentytwenty/dist/vue-twentytwenty.css';
// import TwentyTwenty from '../../node_modules/vue-twentytwenty/src/index';

export default {
  name: 'HelloWorld',
  // components: {
  //   TwentyTwenty
  // },
  data(){
    return {
      readyToSlide : true,
      swiper : "",
      compare1 : require("../assets/compare1.jpg"),
      compare2 : require("../assets/compare2.jpg"),
      isButtonActive : false,
      socmed:[
        {
          name: "Facebook",
          url: "https://www.facebook.com/bryanrinaldoo",
          class : "facebook",
          icon : "fab fa-facebook-f"
        },
        {
          name: "Twitter",
          url: "https://twitter.com/bryanrinaldoo",
          class : "twitter",
          icon : "fab fa-twitter"
        },
        {
          name: "Github",
          url: "https://github.com/bryanrinaldoo",
          class : "github",
          icon : "fab fa-github"
        },
        {
          name: "Instagram",
          url: "https://www.instagram.com/bryanrinaldoo/",
          class : "instagram",
          icon : "fab fa-instagram"
        },
        {
          name: "LinkedIn",
          url: "https://www.linkedin.com/in/bryanrinaldoo/",
          class : "linkedin",
          icon : "fab fa-linkedin-in"
        },
        
      ],
      member:[
        { 
          name: "Nayeon",
          birthday: "September 22, 1995",
          emoji: "🐰",
          vlog:"https://www.youtube.com/watch?v=28Avip-paeA",
          background: "section1",
          colour: "skyBlue"
        },
        { 
          name: "Jeongyeon",
          birthday: "November 1, 1996",
          emoji: "🐶",
          vlog:"https://www.youtube.com/watch?v=t4eIRbA4zw8",
          background: "section2",
          colour: "YellowGreen"
        },
        { 
          name: "Momo",
          birthday: "November 9, 1996",
          emoji: "🐻",
          vlog:"https://www.youtube.com/watch?v=fDwoc1darYk",
          background: "section3",
          colour: "pink"
        },
        { 
          name: "Sana",
          birthday: "December 29, 1996",
          emoji: "🐹",
          vlog:"https://www.youtube.com/watch?v=CPcvaBmrD60",
          background: "section4",
          colour: "#CF9FFF"
        },
        { 
          name: "Jihyo",
          birthday: "February 1, 1997",
          emoji: "🦄",
          vlog:"https://www.youtube.com/watch?v=CYicpmxKyME",
          background: "section5",
          colour: "Apricot"
        },
        { 
          name: "Mina",
          birthday: "March 24, 1997",
          emoji: "🐧",
          vlog:"https://www.youtube.com/watch?v=7kV7urmtsWE",
          background: "section6",
          colour: "#3eb489"
        },
        { 
          name: "Dahyun",
          birthday: "May 28, 1998",
          emoji: "🐷",
          vlog:"https://www.youtube.com/watch?v=xBDECHE0Qig",
          background: "section7",
          colour: "white"
        },
        { 
          name: "Chaeyoung",
          birthday: "April 23, 1999",
          emoji: "🐯",
          vlog:"https://www.youtube.com/watch?v=eMpMgEyp7yg",
          background: "section8",
          colour: "#E84B4F"
        },
        { 
          name: "Tzuyu",
          birthday: "June 14, 1999",
          emoji: "🦌",
          vlog:"https://www.youtube.com/watch?v=sgey4Z91Xd8",
          background: "section9",
          colour: "#6495ED"
        },
      ],
      albums: [
        {
          name: "Like OOH-AHH",
          image: require("../assets/1.png"),
          url: "https://youtu.be/0rtV5esQT6I"
        },
        {
          name: "CHEER UP",
          image: require("../assets/2.png"),
          url: "https://youtu.be/c7rCyll5AeY"
        },
        {
          name: "TT",
          image: require("../assets/3.png"),
          url: "https://youtu.be/ePpPVE-GGJw"
        },
        {
          name: "KNOCK KNOCK",
          image: require("../assets/4.jpg"),
          url:"https://youtu.be/8A2t_tAjMz8"
        },
        {
          name: "Signal",
          image: require("../assets/5.jpg"),
          url: "https://youtu.be/VQtonf1fv_s"
        },
        {
          name: "LIKEY",
          image: require("../assets/6.png"),
          url: "https://youtu.be/V2hlQkVJZhE"
        },
        {
          name: "Heart Shaker",
          image: require("../assets/7.jpg"),
          url: "https://youtu.be/rRzxEiBLQCA"
        },
        {
          name: "What is Love?",
          image: require("../assets/8.png"),
          url: "https://youtu.be/i0p1bmr0EmE"
        },
        {
          name: "Dance The Night Away",
          image: require("../assets/9.jpg"),
          url: "https://youtu.be/Fm5iP0S1z9w"
        },
        {
          name: "YES or Yes",
          image: require("../assets/10.jpg"),
          url: "https://youtu.be/mAKsZ26SabQ"
        },
        {
          name: "Fancy",
          image: require("../assets/11.jpg"),
          url: "https://youtu.be/kOHB85vDuow"
        },
        {
          name: "Feel Special",
          image: require("../assets/12.jpg"),
          url: "https://youtu.be/3ymwOvzhwHs"
        },
        {
          name: "More & More",
          image: require("../assets/13.jpg"),
          url: "https://youtu.be/mH0_XpSHkZo"
        },
        {
          name: "I Can’t Stop Me",
          image: require("../assets/14.jpg"),
          url: "https://youtu.be/CM4CkVFmTds"
        },
        {
          name: "Alcohol-Free",
          image: require("../assets/15.jpg"),
          url: "https://youtu.be/XA2YEHn-A8Q"
        },
        {
          name: "Scientist",
          image: require("../assets/16.jpg"),
          url: "https://youtu.be/vPwaXytZcgI"
        },
      ]
    }
  },

  mounted() {
    this.swiper = new Swiper(this.$refs.swiper, {

      // configure Swiper to use modules
      effect: "fade",
      fadeEffect: { crossFade: true },
      // speed: 1500,
      // slidesPerView: 1,
      // autoplay: { delay: 5000 },


      modules: [Pagination, EffectFade, Mousewheel],
      allowTouchMove: false,

      // Optional parameters
      direction:"vertical",
      

      /**
       * ? ttp gaguna
       */
      mousewheel: true,

      // If we need pagination
      pagination: {
        el: '.swiper-pagination',
        clickable: true
      },

    })
    this.swiper;

    if(this.swiper.activeIndex==0){
      console.log(this.isButtonActive);
      this.isButtonActive = false;
    }else{
      this.isButtonActive = true;
    }

    // const self = this
    // window.addEventListener("wheel", event => {
    //     if(event.deltaY > 0){
    //       if(self.readyToSlide){
    //         self.swiper.slideNext();
    //       }
    //     }else{
    //       if(self.readyToSlide){
    //         self.swiper.slidePrev();
    //       }
    //     }
    //     self.readyToSlide = false;
    // });
    // this.swiper.on("transitionEnd", ()=>{
    //   this.readyToSlide = true;
    //   console.log('transition');
    // })

    // ALBUM
    var swiperAlbum = new Swiper(this.$refs.swiperAlbum, {

      // configure Swiper to use modules
      modules: [Navigation, Pagination],

      // Optional parameters
      speed: 500,
      effect: 'fade',
      loop: true,
      nested: true,

      // If we need pagination
      pagination: {
        el: '.swiper-pagination-album',
        clickable: true
      },

      // Navigation arrows
      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      },
    })
    swiperAlbum;
  },

  methods: {
    chooseMember: function(){
      this.swiper.slideTo(2)
    },
    chooseAlbum: function(){
      this.swiper.slideTo(11)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Lexend+Deca&display=swap');
@import url('https://fonts.googleapis.com/css?family=Montserrat');
.containerPage {
    font-family: 'Lexend Deca', sans-serif;
    margin: 0;
    padding: 0;
    text-decoration: none;
    list-style: none;
    box-sizing: border-box;
    /* margin: var(--top-spacing) auto; */
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

img {
  display: inline-block;
  vertical-align: middle;
  max-width: 100%;
  height: auto;
  -ms-interpolation-mode: bicubic;
}

.containerPage{
  height: 100%;
  width: 100%;
  position: relative;
}

.swiper {
  width: 100%;
  height: 100%;
}
.swiper-slide{
  /* height: 100vh; */
  width: 100%;
  position: relative;
  text-align: center;
  font-size: 18px;
  background: #fff;

  display: table;
  table-layout: fixed;
  width: 100%;
  
  visibility: hidden;
  opacity: 0;
  z-index: 0;

  transition: all .45s ease-in-out;
}
.swiper-slide .album{
  padding-top: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.swiper-slide .album img{
  max-height: 600px;
}
.swiper-slide img {
  display: block;
}

.swiper-slide-active{
  visibility: visible !important; 
  opacity: 1;
  z-index: 1;
}

.content{
  display: table-cell;
  vertical-align: middle;
  width: 100%;
  height: 100%;
}
.content.choose{
  display: flex;
  justify-content: center;
}

.choose1, .choose2{ 
  width: 100%;
}

.compareContent{
  width: 100%;
  height: 100%;
  position: relative;
}
.twentytwenty-container{
  width: 100% !important;
  height: 100% !important;
}

.twentytwenty-container img{
  width:100% !important;
  height:100% !important;
}

.menu1{
  display: flex;
  align-items: center;
  justify-content: center;
  justify-items: center;
}
.menu1 h3 {
    font-size: 70px;
    color: #fe97a4;
    text-transform: uppercase;
}
.bgColor1{
  background: #fdb4a5bc !important;
}
.bgColor2{
  background: #fe7ba3 !important;
}
.backgroundChooseSection{ 
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  z-index: 0;
}

.backgroundChooseSection p{
  font-size: 80px;
  color: black;
  opacity: 1;
  transition: 1s;
  cursor: pointer;
}
.backgroundChooseSection p:hover{
  font-size: 90px;
}
.nameSection{ 
  z-index: 3;
  position: absolute;
  right: 5%;
  bottom: 10%;
  transform: translate(-10%, -20%);
}

.nameSection h2{
  font-size: 80px;
}

.backgroundSection{ 
  width: 100%;
  height: 100vh;
  position: absolute !important;
  left: 0;
  top: 0;
  z-index: 0;
  transform: scale(1.3);
}

.buttonSection{
  position: absolute;
  bottom: 10%;
  left: 5%;
  z-index: 25;
  cursor: pointer;
}

.buttonSectionAlbum{
  position: absolute;
  bottom: -2%;
  left: 5%;
  z-index: 25;
  cursor: pointer;
}

.buttonMore.albumBtn{
  border-radius: 40px;
  height: 35px;
  max-width: 35px;
}
.buttonMore.albumBtn .icon{
  font-size: 17px;
  padding: 0px 6px;
}

.buttonMore {
  background-color: #fccfa6;
  color: #333333;
  text-decoration: none;
  border-radius: 60px;
  height: 70px;
  display: inline-flex;
  align-items: center;
  overflow:hidden;
  width: auto;
  max-width: 70px;
  -webkit-transition: max-width 0.5s;
  transition: max-width 0.5s;
}

.buttonMore:hover {
  max-width: 300px;
}

.buttonMore .icon {
  font-size: 40px;
  margin-right: 15px;
  padding: 0px 8px;
  display: flex;
  align-items: center;
}

.buttonMore .text {
  white-space: nowrap;
  padding-right: 15px;
}

.background{
  background-size: cover;
  background-repeat: no-repeat;
  opacity: 0.5;
}
.choose1Pic{
  background-image: url("../assets/choose1.jpg");
}
.choose2Pic{
  background-image: url("../assets/choose2.jpg");
}
.section1{ 
  background-image: url("../assets/sec1.jpg");
}
.section2{ 
  background-image: url("../assets/sec2.jpg");
}
.section3{ 
  background-image: url("../assets/sec3.jpg");
}
.section4{ 
  background-image: url("../assets/sec4.jpg");
}
.section5{ 
  background-image: url("../assets/sec5.jpg");
}
.section6{ 
  background-image: url("../assets/sec6.jpg");
}
.section7{ 
  background-image: url("../assets/sec7.jpg");
}
.section8{ 
  background-image: url("../assets/sec8.jpg");
}
.section9{ 
  background-image: url("../assets/sec9.jpg");
}

.swiper-pagination {
  color: #42b983;
}
.swiper-button-prev,
.swiper-button-next{
  color: #794515;
}

.profilePic{
  width: 500px;
}

.socmed{
  display: inline-flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
}

.icon {
  margin: 0 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  cursor: pointer;
  position: relative;
  z-index: 2;
}

.icon span i {
  color: black;
  line-height: 60px;
  font-size: 25px;
}
.icon:hover span i {
    color: white;
}

.icon span {
    height: 60px;
    width: 60px;
    display: block;
    background: rgb(241, 241, 241);
    text-align: center;
    border-radius: 50%;
    box-shadow: 0 10px 10px rgba(0, 0, 0, .1);
    margin-right: 50px;
}

.icon .tooltip {
    position: absolute;
    top: 0px;
    background: rgb(241, 241, 241);
    color: white;
    font-size: 20px;
    padding: 10px 18px;
    border-radius: 25px;
    box-shadow: 0 10px 10px rgba(0, 0, 0, .1);
    opacity: 0;
    pointer-events: none;
    transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    margin-right: 50px;
}

.icon:hover .tooltip {
    top: 70px;
    opacity: 1;
    pointer-events: auto;
}

.icon .tooltip:before {
    position: absolute;
    content: "";
    height: 15px;
    width: 15px;
    background: rgb(241, 241, 241);
    top: -6px;
    left: 50%;
    transform: translateX(-50%) rotate(45deg);
    transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.icon:hover span,
.icon:hover .tooltip {
    text-shadow: 0px -1px 0px rgba(0, 0, 0, .4);
}

.facebook:hover span,
.facebook:hover .tooltip,
.facebook:hover .tooltip::before {
    background: #3b5999;
}

.twitter:hover span,
.twitter:hover .tooltip,
.twitter:hover .tooltip::before {
    background: #46c1f6;
}

.instagram:hover span,
.instagram:hover .tooltip,
.instagram:hover .tooltip::before {
    background: #e1306c;
}
.github:hover span,
.github:hover .tooltip,
.github:hover .tooltip::before {
    background: #333;
}

.linkedin:hover span,
.linkedin:hover .tooltip,
.linkedin:hover .tooltip::before {
    background: #0e76a8 
}

/* ANIMATION */

.menu1 .logoMenu {
    width: 500px;
    animation: float 3s linear infinite;
}

@keyframes float {

    0%,
    100% {
        transform: translateY(0px)
    }

    50% {
        transform: translateY(-10px)
    }
}

@keyframes all {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
.swiper-slide-active .zoom_animation {
    animation: zoom 5s forwards ease-out;
}

@keyframes zoom {
  0% {
    transform: scale(1.5, 1.5);
  }
  100% {
    transform: scale(1.2, 1.2);
  }
}

.swiper-slide-active .animateText{
  animation: animate-to-top 0.5s linear;
}

@keyframes animate-to-top {
  0% {
    transform: translateY(150%);
  }
  100% {
    transform: translateY(0%);
  }
}


</style>
