<template lang="pug">
  section#hero
    .bg-container
      .hero-video
        video( poster="./images/misc/bg-slide1.jpg" playsinline autoplay loop muted )
          source( type="video/mp4" src="~static/video/bg.mp4" )
      //- .bg.bg1
        .typo
          h1
            | 持続可能な資産運用を
            br
            | 誠実にサポート
      //- agile( :options="options" ref="carousel" @after-change="e => currentSlide = e.currentSlide" )
      .bg-slides
        .bg.bg1( :class="{ 'active': this.currentSlide === 0 }" )
          .typo
            h1
              | 持続可能な資産運用を
              br
              | 誠実にサポート
        .bg.bg2( :class="{ 'active': this.currentSlide === 1 }" )
          .inner
            .typo
              .tagline
                | 一生涯マンツーマン型
        .bg.bg3( :class="{ 'active': this.currentSlide === 2 }" )
          .inner
            .typo
              .tagline
                | 最新のマネートレンド
        .bg.bg4( :class="{ 'active': this.currentSlide === 3 }" )
          .inner
            .typo
              .tagline
                | 継続的な価値ある提案
      .button
        //- nuxt-link( v-scroll-to="'#contact'" to )
        a( href="https://forms.gle/kKj8qcvpc3HmzLVn7" target="_blank" rel="noopener noreferrer nofollow" )
          .icon
            IconArrow
          .text
            | お問い合わせ

    .card-list
      .card( @mouseover="changeSlide(1)" @mouseleave="resetSlide()" )
        .content
          img( src="~/static/images/icon/umbrella.svg" )
          .text
            | 安心
            span with strong security
      .card( @mouseover="changeSlide(2)" @mouseleave="resetSlide()" )
        .content
          img( src="~/static/images/icon/timer.svg" )
          .text
            | 最新
            span resourceful information
      .card( @mouseover="changeSlide(3)" @mouseleave="resetSlide()" )
        .content
          img( src="~/static/images/icon/roadmap.svg" )
          .text
            | 継続
            span continuous support

</template>
<script>
import IconArrow from '~/static/images/icon/arrow.svg?inline'

export default {
  components: {
    IconArrow
  },
  data () {
    return {
      currentSlide: 0,
      /*
      options: {
        fade: true,
        autoplay: true,
        autoplaySpeed: 7500,
        navButtons: false,
        // pauseOnHover: false,
        dots: false
      }*/
    }
  },
  methods: {
    changeSlide(val) {
      // console.log(val)
      this.currentSlide = val
      // console.log(this.currentSlide)
    },
    resetSlide() {
      this.currentSlide = 0
    }
  }
}
</script>

<style lang="stylus" scoped>
#hero
  display flex
  // min-height calc(100vh - 80px)
  @media (max-width: 767px)
    flex-wrap wrap
.bg-container
  position relative
  width 66.6666vw
  height calc(100vh - 80px)
  @media (max-width: 767px)
    width 100%
    height calc(75vh - 80px)
  @media (max-width: 639px)
    height calc(80vh - 50px)
  .hero-video
    video
      position absolute
      top 0
      left 0
      width 100%
      max-width 100%
      height 100%
      object-fit cover
      z-index -1
    &::after
      content ''
      position absolute
      top 0
      left 0
      width 100%
      height 100%
      background rgba(35, 24, 21, .8)
      z-index 0
  .bg
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    // height calc(100vh - 80px)
    padding 40px
    transition opacity .2s, visibility .2s
    opacity 0
    visibility hidden
    z-index 1
    @media (max-width: 639px)
      padding 20px
    &.bg2, &.bg3, &.bg4
      display flex
      align-items center
      justify-content center
      padding-bottom 100px
      .typo
        position relative
        padding-bottom 30px
        overflow hidden
        &::before
          content ''
          position absolute
          left 0
          bottom 0
          width 100%
          border-bottom 1px solid $primary
          transform translateX(-100%)
          transition transform .75s ease-in-out .2s
    &.active
      opacity 1
      visibility visible
      .typo::before
        transform translateX(0)
    /*
    .inner.active
      .typo::before
        transform translateX(0)
    */
  .typo
    h1
      display inline-block
      padding-bottom 40px
      color $white
      font-size 48px
      font-weight 300
      border-bottom 1px solid $primary
      @media (max-width: 1279px)
        font-size 40px
      @media (max-width: 1023px)
        font-size 32px
      @media (max-width: 639px)
        font-size 24px
  .tagline
    color $textContrast
    font-size 32px
    font-weight normal
    text-align center
    @media (max-width: 1279px)
      font-size 26px
    @media (max-width: 1023px)
      font-size 22px
    @media (max-width: 639px)
      font-size 20px
  .button
    position absolute
    left 40px
    bottom 50px
    z-index 9999
    @media (max-width: 639px)
      left 20px
      bottom 30px
    a
      display flex
      align-items center
      &:hover
        svg
          transform rotate(45deg)
    .icon
      width 60px
      height 60px
      display flex
      align-items center
      justify-content center
      background-color $black
      @media (max-width: 639px)
        width 44px
        height 44px
      svg
        transition transform .25s ease-in-out
    .text
      display flex
      align-items center
      justify-content center
      color $white
      width 200px
      height 60px
      background-color $red
      @media (max-width: 639px)
        width 160px
        height 44px

.card-list
  width 33.3333vw
  @media (max-width: 767px)
    display flex
    align-items center
    justify-content center
    flex-wrap wrap
    width 100%
    height 25vh
  @media (max-width: 639px)
    // height auto
    height 20vh
  .card
    position relative
    width 100%
    height 33.3333%
    color $white
    background-color $black
    border-bottom 1px solid $whiteTransparent2
    overflow hidden
    @media (max-width: 767px)
      width 33.333vw
      height 100%
    /*@media (max-width: 639px)
      width 100vw
      height auto*/
    &:before
      content ''
      position absolute
      top 0
      left 0
      background-color $primary
      width 100%
      height 100%
      transition transform .4s ease-in-out
      transform translateY(100%)
      z-index 0
    &:hover,
    &.active
      &:before
        transform translateY(0)
    &:last-child
      border 0
    .content
      position relative
      width 100%
      height 100%
      display flex
      align-items center
      justify-content space-between
      padding 40px
      @media (max-width: 639px)
        flex-wrap wrap
        justify-content center
        padding 20px
    img
      width 120px
      height 120px
      @media (max-width: 1279px)
        width 100px
        height 100px
      @media (max-width: 767px)
        width 60px
        height 60px
        align-self flex-start
      @media (max-width: 639px)
        width 44px
        height 44px
    .text
      align-self flex-end
      font-size 32px
      text-align right
      letter-spacing .1rem
      @media (max-width: 1279px)
        font-size 28px
      @media (max-width: 767px)
        font-size 20px
      @media (max-width: 639px)
        width 100%
        font-size 16px
        text-align center
      span
        display block
        color $textContrastMuted
        font-size 18px
        @media (max-width: 1279px)
          font-size 16px
        @media (max-width: 767px)
          font-size 14px
        @media (max-width: 639px)
          display none
</style>