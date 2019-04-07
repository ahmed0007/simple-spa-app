<template>
  
  <section class="container">

    <div class="top-left">

      <BaseButton 
      
            :round="true" 

              :unique="'image1'"

                :current="currentImage"
            
              @click="loadImage1">image1</BaseButton>

    </div>
      
      <div class="centered">

   
        <div >

          <image-preview  :preview="image"  @close="currentImage=''" ></image-preview>

        </div>

        <div>

          <BaseButton :round="true" 


              :unique="'image2'"

                :current="currentImage"

          
                @click="loadImage2">image2</BaseButton>  

        </div>
   
      </div>

    <div class="bottom-left">

      <BaseButton 
      
            :round="true"

              :unique="'image3'"

                :current="currentImage"

           
            
                @click="loadImage3">image1
                
                    </BaseButton>

    </div>

  
  </section>

</template>

<script>

import BaseButton from '@/components/BaseButton'

import ImagePreview from '@/components/ImagePreview'

export default {
  
  components: {

    BaseButton,

    ImagePreview

  },

  data(){


    return {

      image : "default-avatar.png",

      currentImage : '',

      loading: false,

    }

  },

  methods:{

      loadImage1(){

        this.currentImage = 'image1';
        this.image = 'anime3.png';

      },
      
      loadImage2(){


        this.currentImage = 'image2';
        
        this.image = 'anime6.png';




      },


      loadImage3(){

        this.currentImage = 'image3';

        this.image = 'apple-icon1.png';

      }


    }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.top-left{

    align-self: flex-start;
    
    left: 50px;
    
    top: 100px;
    
    position: absolute;

}

.bottom-left{

    align-self: flex-start;
    
    left: 50px;
    
    bottom: 100px;
    
    position: absolute;

}

.centered{

    display: flex;
    width: 100%;
    flex-direction: row;
    justify-content: space-around;

}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
