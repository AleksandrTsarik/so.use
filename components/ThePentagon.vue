<template>
  <div class="pentagon row" v-if="type === 'bootstrap'">
    <div class="pentagon__item col-xl-3 col-lg-4 col-md-6 col-sm-12 mb-3 ms-auto me-auto" v-for="(item, i) in imgPath" :key="i">
      <svg version="1.1" width="250" height="250" viewBox="0 0 100 100">  
      <defs>
        <mask id="msk1" >
          <g fill="white">
            <path d="M20,0 L80,0 L100,60 L50,100 L0,60z" x="0" y="0" stroke="black" />
          </g>
        </mask>
        </defs>
        <image :xlink:href="item.img" mask="url(#msk1)" class="pentagon__img" width="100%" height="100%" />
      </svg>
    </div>
  </div>

  <div class="pentagon" v-else>
    <div class="pentagon__item" v-for="(item, i) in imgPath" :key="i">
      <svg version="1.1" width="250" height="250" viewBox="0 0 100 100">  
      <defs>
        <mask id="msk1" >
          <g fill="white">
            <path d="M20,0 L80,0 L100,60 L50,100 L0,60z" x="0" y="0" stroke="black" />
          </g>
        </mask>
        </defs>
        <image :xlink:href="item.img" mask="url(#msk1)" class="pentagon__img" width="100%" height="100%" />
      </svg>	
    </div>
  </div>


 
</template>


<script>
export default {
  props: {
    imgPath: {
      type: String
    },
    type: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">

  .pentagon{
    &__item {
      display: inline-block;
    }
    svg {
      position: relative;
      overflow: hidden;
      width: 250px;
      height: 250px;
      display: block;
      margin: 0 auto;
      &:hover image{
        width: 130%;
        height: 130%;
      }
    }
    &__img {
      transition: 0.3s;
    }

  }
</style>