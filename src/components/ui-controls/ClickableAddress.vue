<template>
  <span v-if="ethAddress">
    <a class="token-id" :href="buildLink" target="_blank">{{ dotDotDot }}</a>
  </span>
</template>

<script>
  /* global web3:true */
  import EthAddress from './EthAddress';
  import { mapGetters, mapState } from 'vuex';

  export default {
    name: 'addressIcon',
    components: {EthAddress},
    props: {
      ethAddress: {
        type: String
      }
    },
    computed: {
      ...mapState([
        'etherscanBase',
      ]),
      dotDotDot: function () {
        if (this.ethAddress) {
          return this.ethAddress.substr(0, 6) + '...' + this.ethAddress.substr(this.ethAddress.length - 6, this.ethAddress.length);
        }
        return str;
      },
      buildLink: function () {
        return `${this.etherscanBase}/address/${this.ethAddress}`;
      }
    }
  };
</script>

<style>
  .icon-normal {
    height: 64px;
    width: 64px;
  }

  .icon-small {
    height: 32px;
    width: 32px;
  }
</style>
