<template lang="pug">
  header.header
    .wrapper(@click='toggleNav(true)')
      nuxt-link.logo(to="/")
        span.visually-hidden Vue mastery
        img(src="/images/logo.png" role="logo" alt="Vue Mastery logo")

      navigation(:account='account' @closeNav='toggleNav(true)')
    hambuger(@toggleNav='toggleNav()')
</template>

<script>
import navigation from './Navigation'
import hambuger from './Hamburger'
import { mapState, mapActions } from 'vuex'

export default {
  name: 'top',
  components: {
    navigation,
    hambuger
  },
  computed: {
    ...mapState({
      account: result => result.account.account
    })
  },
  methods: {
    ...mapActions(['toggleNav'])
  }
}
</script>

<style lang="stylus">
.open-nav
  .logo
    transform: translateX(-50%)
    margin-left: 50%
</style>

<style lang="stylus" scoped>
@import '~assets/css/_variables'

.header
  position relative
  z-index 2
  .wrapper
    height $header-height
    display flex
    flex-wrap wrap
    align-items center

.logo
  display block
  max-width 200px
  margin-top -5px
  position: relative
  z-index: 1
  transition: all ease-in .2s

  img
    display block
    width 100%

  +laptop-up()
    transform: none
    max-width 282px
    min-width 200px
    margin: -10px 70px 0 0
</style>
