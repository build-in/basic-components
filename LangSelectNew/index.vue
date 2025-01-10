<template>
  <div class="lanage-contanier">
    <img class="lange-icon" v-if="language !== 'zh'" @click="handleSetLanguage('zh')" :src="getImage('zhLange')" alt="">
    <img class="lange-icon" v-else @click="handleSetLanguage('en')"  :src="getImage('enlange')" alt="">
  </div>
</template>

<script>
import { getImages } from '@/views/dashboard/common';
export default {
  computed: {
    language() {
      return this.$store.getters.language
    }
  },
  methods: {
    handleSetLanguage(lang) {
      if(this.$store.getters.currentSysCode === 'omc') {
        this.$i18n.locale = lang
      }
      console.log(lang,'langlanglanglanglang');
      this.$store.dispatch('setLanguage', lang)
      this.$message({
        message: 'switch language success',
        type: 'success'
      })
    },
    getImage(name){
        const newVal = getImages.filter((v)=>{
         return v.name === name;
        });
        return require(`@/${newVal[0].src}`)
      },
  }
}
</script>

<style lang="scss" scoped>
.international-icon {
  font-size: 20px;
  cursor: pointer;
  vertical-align: -5px!important;
}
.lange-icon{
  width:20px;
  height: 20px;
  object-fit: contain;
}
.lanage-contanier{
  cursor: pointer;
}
</style>


