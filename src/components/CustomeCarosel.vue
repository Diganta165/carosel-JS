<template>
  <div>
      <div class="carosel-section">
          <div class="image-section " >
              
             <transition name = 'fade'>
                  <img v-if="show" class='image-slider fade'  style=" width: 100%" id="selectImage"  :src = 'images[index]' @mouseover="stopSlider()" @mouseleave="showSlider()" />
             </transition>
                
          </div>
          <a class="prev" @mouseover="stopSlider()" @click="previousSlide()" @mouseleave="showSlider()">&#10094;</a>
                <a class="next" @mouseover="stopSlider()" @click="nextSlide()" @mouseleave="showSlider()">&#10095;</a>
      </div>


      <section id="company_testimonial" class="company_testimonial_area">    
        <div class="container carosel-section">
            <div class="company_testimonial_wrapper">
                <div class="company_testimonial_title common_heading_title txt_center mb50">
                    <h4>What Our <span> Clients Say?</span></h4>
                </div>
                <div class="company_testimonial_inner_content">
                  
                    
                    <div class="company_testimonial_carousel">
                 
                        
                        <div class="company_testimonial_carousel_content mb47">
                            <p class="clients_message">
                                "em ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy.''
                            </p>
                            <div class="clients_profile_title">
                                <div class="clients_profile_image">
                                    <!-- <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="55" height="55" viewBox="0 0 55 55">
                                        <defs>
                                          <pattern id="pattern" preserveAspectRatio="xMidYMid slice" width="100%" height="100%" viewBox="0 0 200 200">
                                            <image width="200" height="200" xlink:href="data:image/jpeg;base64,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"/>
                                          </pattern>
                                        </defs>
                                        <circle id="Ellipse_33" data-name="Ellipse 33" cx="27.5" cy="27.5" r="27.5" fill="url(#pattern)"/>
                                      </svg> -->
                                      <img class='image-slider fade'  style=" width: 100%" id="selectImage"  :src = 'images[index]' @mouseover="stopSlider()" @mouseleave="showSlider()" />
                                </div>
                                <div class="clients_profile_title">
                                    <p>Mr. Abc Ahmed</p>
                                    <span>CEO, Abc Ltd</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
               
                
                <div class="clients_testimonial_carousel_dots d_flex align_center justify_center">
                    <div class="dot dot_One "></div>
                    <div  :class ="sliderLeftActive == false ? 'dot dot_two' : 'dot dot_two active_carousel'  " @mouseover="stopSlider()" @click="previousSlide()" @mouseleave="showSlider()"></div>
                    <div class="dot dot_three active_carousel"></div>
                    <div :class ="sliderRightActive == false ? 'dot dot_four' : 'dot dot_four active_carousel'  " @mouseover="stopSlider()" @click="nextSlide()" @mouseleave="showSlider()"></div>
                    <div class="dot dot_five"></div>
                </div>
            </div>
            <a class="prev" @mouseover="stopSlider()" @click="previousSlide()" @mouseleave="showSlider()">&#10094;</a>
            <a class="next" @mouseover="stopSlider()" @click="nextSlide()" @mouseleave="showSlider()">&#10095;</a>
        </div>
    </section>
  </div>
</template>

<script>

export default {
    data(){
        return{
           
            images:[
                '/images/beastMaster.png',
                '/images/marci.png',
                '/images/mars.png',
                '/images/tinker.png',
            ],
            index:0,
            sliderType:'',
            sliderLeftActive: false,
            sliderRightActive:false,
            show: false
        }
    },

    methods:{
       
       

        showSlider(){
            
            console.log('hi',this.index)
            let selectImage = document.getElementById('selectImage')
            // this.index = 0 
            this.sliderType =  setInterval(()=>{
                console.log('Inside time interval',this.index)
                if(this.index >= this.images.length-1){
                    this.index = 0
                    selectImage.setAttribute('src',this.images[this.index])
                }else if(this.index < 0){
                    console.log('Array Length', this.images.length)
                    this.index = this.images.length-1
                    selectImage.setAttribute('src',this.images[this.index])
                    
                }else{
                    console.log('showSlider else index', this.index)
                    ++ this.index
                    selectImage.setAttribute('src',this.images[this.index])
                }
                // selectImage.setAttribute('src',this.images[this.index])  

        },2000)

            
        
        },
         nextSlide(){
             this.show = true
            this.sliderLeftActive = false
            this.sliderRightActive = true

             console.log('Next slide',this.index)
             console.log('Image Length',this.images.length)
            // this.index++
            if(this.index > this.images.length-1){
                console.log('Indise if',this.index)
                this.index = 0 
            }else{
                // this.index++;
                this.index++;
                if(this.index === 4){
                    this.index = 0
                }
            }
            // this.showSlider()
            console.log(this.index)
        },
        previousSlide(){
            this.show = true
            this.sliderLeftActive = true
            this.sliderRightActive = false
            // this.index--
            if(this.index <= 0){
                this.index = this.images.length-1
            }else{
               
                this.index--;
                if(this.index === -1){
                    this.index = 3
                }
            }
            console.log(this.index)
            // this.showSlider()
            // this.showSlider(this.index--)
        },

         stopSlider(){
            clearInterval(this.sliderType)
        },

        // showSlider(sliderNo){

            // const sliderElement = document.getElementById('image-slider')
            // if(sliderNo > images.length ){
            //     this.index = 0
            // }else if(sliderNo < 0){
            //     this.index = images.length
            // }

            // for(let i = 0; i < this.images.length; i++){
            //     // sliderElement.setAttribute(src)
            // }


            
        },
        mounted(){
            this.showSlider()
        }


    }

</script>

<style>
@import '../../public/css/testimonial.css';
@import '../../public/css/global.css';
/* @import '../../public/css/icofont.min.css'; */
@import '../../public/css/responsive.css';
.carosel-section{
    /* display: flex;
    justify-content: center;
    padding: 10px; */
  max-width: 1000px;
  position: relative;
  margin: auto;

}
.image-slider{
    position: relative;
    /* transition-timing-function: linear */
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -22px;
  padding: 16px;
  color: black;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 0 3px 3px 0;
  user-select: none;
}
.next {
  right: 0;
  border-radius: 3px 0 0 3px;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.8);
}
/* .fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1.5s;
  animation-name: fade;
  animation-duration: 1.5s;
}
@-webkit-keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
}

@keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
} */


.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>