<template lang="pug">
modal.tm-modal-help(v-if="active" :close="close")
  div(slot='title') Need Help?
  p Something in the app not working correctly? Tell us what went wrong in developer chat or create an issue on our GitHub. Thanks for improving Cosmos Voyager!
  tm-list-item(
    title="Developer Chat"
    href="https://riot.im/app/#/room/#cosmos:matrix.org")
  tm-list-item(
    title="GitHub Issues"
    href="https://github.com/cosmos/voyager/issues")
</template>

<script>
import { mapGetters } from "vuex"
import Modal from "common/TmModal"
import { TmListItem } from "@tendermint/ui"
export default {
  name: "tm-modal-help",
  components: {
    TmListItem,
    Modal
  },
  computed: {
    ...mapGetters(["config"]),
    active() {
      return this.config.modals.help.active
    }
  },
  methods: {
    close() {
      this.$store.commit("setModalHelp", false)
    }
  }
}
</script>

<style lang="stylus">
@import '~variables'

.tm-modal.tm-modal-help
  z-index z(modalHelp)

  .tm-modal-main
    padding 2rem

    p
      margin 0 0 2rem
</style>
