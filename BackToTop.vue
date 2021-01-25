<template>
  <div>
    <a
      id="back2top"
      href="javascript:void(0)"
      class="back2top"
      role="button"
      @click="backToTop"
    >
      <i class="fa fa-chevron-up" />
    </a>
  </div>
</template>

<script>
export default {
  async mounted () {
    window.smoothscroll = () => {
      const currentScroll = document.documentElement.scrollTop || document.body.scrollTop
      if (currentScroll > 0) {
        window.requestAnimationFrame(window.smoothscroll)
        window.scrollTo(0, Math.floor(currentScroll - (currentScroll / 5)))
      }
    }
    window.addEventListener('scroll', this.scroll)
  },

  methods: {
    backToTop () {
      window.smoothscroll()
    },
    destroyed () {
      window.removeEventListener('scroll', this.scroll)
    },
    scroll () {
      const scrollBtn = document.getElementById('back2top')
      if (document.body.scrollTop > 100 || document.documentElement.scrollTop > 100) {
        scrollBtn.style.display = 'block'
        scrollBtn.style.background = '#00AAEE'
      } else {
        scrollBtn.style.display = 'none'
      }
    }
  }
}
</script>

<style scoped lang="scss">
  html {
    scroll-behavior: smooth;
  }

  .back2top {
    display: none;
    position: fixed;
    bottom: 20px;
    right: 30px;
    z-index: 99;
    font-size: 18px;
    border: none;
    outline: none;
    background-color: #00AAEE;
    color: white;
    cursor: pointer;
    padding: 15px;
    border-radius: 4px;
  }

  .back2top:hover {
    background-color: #757575;
    color: whitesmoke !important;
  }
</style>
