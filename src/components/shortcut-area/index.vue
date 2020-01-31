<template>
  <div>
    <v-container style="padding: 0">
      <v-row style="margin: 0">
        <v-col @click="jump(icon.url)" :md="md" v-for="icon in iconDatas" :key="icon.id" :style="{padding: `0 0 ${marginB}px 0`, margin: 0}">
          <i :class="`iconfont icon-${icon.icon}`" :style="`margin: 0 0 0 25px; font-size: ${icon.size!=null?icon.size:500}%;color:${icon.color}`"></i>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  props: [
    'iconDatas',
    'md',
    'marginB'
  ],
  methods: {
    jump(url) {
      window.open(url,'_self')
    }
  }
}
</script>

<style>

</style>
