<template>
  <div>
    <svg class="hamburger"  @click="toggleClick" :class="{'is-active':isActive}"  viewBox="0 0 20 20" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
      <title>切片</title>
      <g id="9-工作流" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
          <g id="后台框架-方案二" transform="translate(-613.000000, -219.000000)" fill="#303846">
              <g id="ICON/列表图标/1" transform="translate(613.000000, 219.000000)">
                  <rect id="矩形" x="3" y="4" width="14" height="1.5" rx="0.75"></rect>
                  <rect id="矩形备份" x="3" y="9" width="9" height="1.5" rx="0.75"></rect>
                  <rect id="矩形备份-2" x="3" y="14" width="14" height="1.5" rx="0.75"></rect>
                  <path d="M15.9,8.78333333 L17.15,10.45 C17.3156854,10.6709139 17.2709139,10.9843146 17.05,11.15 C16.9634519,11.2149111 16.8581851,11.25 16.75,11.25 L14.25,11.25 C13.9738576,11.25 13.75,11.0261424 13.75,10.75 C13.75,10.6418149 13.7850889,10.5365481 13.85,10.45 L15.1,8.78333333 C15.2656854,8.56241943 15.5790861,8.51764791 15.8,8.68333333 C15.8379028,8.71176046 15.8715729,8.7454305 15.9,8.78333333 Z" id="三角形" transform="translate(15.500000, 9.750000) rotate(-90.000000) translate(-15.500000, -9.750000) "></path>
              </g>
          </g>
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'hamburger',
  props: {
    isActive: {
      type: Boolean,
      default: false
    },
    toggleClick: {
      type: Function,
      default: null
    }
  }
}
</script>

<style scoped>
.hamburger {
  display: inline-block;
  cursor: pointer;
  width: 20px;
  height: 20px;
  transform: rotate(180deg);
  transition: .38s;
  transform-origin: 50% 50%;
}

.hamburger.is-active {
  transform: rotate(0deg);
}
</style>
