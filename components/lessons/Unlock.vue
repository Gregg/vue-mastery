<template lang="pug">
  no-ssr
    .locked-action
      h3 This Lesson Is Locked.
      h5 Create a free account to unlock it.
      button.button.primary.-small.-has-icon(v-cloak @click="openLogin")
        i.fa.fa-unlock-alt
        | Unlock Content
</template>

<script>
export default {
  name: 'unlockButton',
  props: ['courseLink', 'account'],
  methods: {
    openLogin () {
      this.$modal.show('login-form', {
        newAccount: true,
        headerTitle: 'Sign up to Unlock Free Content',
        location: 'Lesson page locked video'
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~assets/css/_variables'
h3,
h4
  padding-top 0

.locked-action
  position absolute
  top 50%
  left 50%
  background #fff
  width 90%
  padding 40px
  text-align center
  transform translate(-50%, -50%)
  border-radius 6px
  border solid 1px #eee
  color $secondary-color

  h5
    font-weight 600

.button
  margin 20px auto 0
</style>
