<template>
  <div class="dashboard-container">
    <el-radio-group v-model="radio" @change="changeLang">
      <el-radio :label="1">zh</el-radio>
      <el-radio :label="2">en</el-radio>
      <el-radio :label="3">tw</el-radio>
    </el-radio-group>
    <div class="dashboard-text">{{ name }}</div>
  </div>
</template>

<script>
// import { mapGetters } from 'vuex'
import Cookies from 'js-cookie'

export default {
  name: 'Dashboard',
  data() {
    return {
      name: this.$t('example.dashboard'),
      radio: 1
    }
  },
  computed: {

  },
  watch: {
  },
  created() {
    // 語系
    switch (Cookies.get('language')) {
      case 'zh':
        this.radio = 1
        break
      case 'en':
        this.radio = 2
        break
      case 'tw':
        this.radio = 3
        break
      default:
        this.radio = 1
        break
    }
  },
  methods: {
    changeLang() {
      console.log(this.radio)
      switch (this.radio) {
        case 1:
          Cookies.set('language', 'zh')
          break
        case 2:
          Cookies.set('language', 'en')
          break
        case 3:
          Cookies.set('language', 'tw')
          break
        default:
          Cookies.set('language', 'zh')
          break
      }
      this.$router.go(0)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
