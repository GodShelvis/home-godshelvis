<template>
  <div>
    <v-row>
      <v-col>
        <v-text-field @keydown.enter="search()" color="black" v-model="input" outlined>
          <template v-slot:append>
            <i @click="search()" :class="`iconfont icon-${chinese?'baidu':'google'}`" color="black" style="font-size: 180%"></i>  
          </template>
        </v-text-field>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: [
    'chinese',
  ],
  data: ()=>{
    return {
      input: ''
    }
  },
  methods: {
    search() {
      window.open(this.chinese?`http://www.baidu.com/s?wd=${this.input}`:`http://www.google.com/search?hl=zh-CN&q=${this.input}`, "_blank");
      this.input = '';
    }
  }
}
</script>

<style>

</style>
