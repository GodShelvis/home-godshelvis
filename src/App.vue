<template>
  <v-app>
    <div class="bg" :style="{width: `${this.clientWidth}px`, height: `${this.clientHeight}px`, backgroundSize: `${this.clientWidth}px ${this.clientHeight}px`}">
      <v-row>
        <v-col md="5" class="black-font pa-0 pl-12">
          <v-row>
            <v-col md="2" style="font-size: 660%; padding: 0 0 0 65px">
              {{YY}}
            </v-col>
            <v-col md="10" style="font-size: 190%; padding: 35px 0 0 200px">
              <div>
                {{date}}
              </div>
              <div>
                {{weekDay}}
              </div>
            </v-col>
          </v-row>
        </v-col>
        <v-col md="6" class="pa-0 pl-12">
          <div class="black-font" align="center" style="padding-top: 20px">
            <transition>
              <span v-if="!chinese" style="font-size: 400%">GodShelvis.com</span>
            </transition>
            <transition>
              <span v-if="chinese" style="font-size: 400%;font-family: Arial">SHELVIS的主页</span>
            </transition>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col md="1" style="font-size: 350%; padding: 0 0 0 100px">
          {{time}}
        </v-col>
        <v-col md="3" offset-md="8" class="pink-font pa-0 pr-12" align="end">
          <transition>
            <span v-if="!chinese" style="font-size: 220%">- YDC Studio</span>
          </transition>
          <transition>
            <span v-if="chinese" style="font-size: 220%">- 雨東山工作室</span>
          </transition>
        </v-col>
      </v-row>
      <v-row>
        <v-col md="5">
          <search-area style="margin: 20px 0 0 90px" :chinese="chinese"></search-area>
        </v-col>
      </v-row>
      <div class="d-flex align-end" :style="`height: ${this.clientHeight-396}px`">
        <v-row :style="{padding: `0 0 ${this.clientHeight*0.045}px 100px`, margin: 0}">
          <v-col md="4" style="padding: 0">
            <shortcut-area :iconDatas="iconData1" :md="6" :marginB="this.clientHeight*0.05" style="margin: 0 0 0 0"></shortcut-area>
          </v-col>
          <v-col md="8" style="padding: 0">
            <shortcut-area :iconDatas="iconData2" :md="3" :marginB="this.clientHeight*0.05" style="margin: 0 0 0 0"></shortcut-area>
          </v-col>
        </v-row>
      </div>
    </div>
  </v-app>
</template>

<script>
import SearchArea from './components/search-area'
import ShortcutArea from './components/shortcut-area'

export default {
  name: 'App',
  components: {
    'search-area': SearchArea,
    'shortcut-area': ShortcutArea,
  },
  data(){
    return{
      clientHeight: document.documentElement.clientHeight,
      clientWidth: document.documentElement.clientWidth,
      chinese: false,
      date: '',
      yy: '',
      time: '',
      weekDay: '',
      chineseWeeks: ['周日','周一','周二','周三','周四','周五','周六'],
      englishWeeks: ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'],
      chineseMonths: ['一月','二月','三月','四月','五月','六月','七月','八月','九月','十月','十一月','十二月'],
      englishMonths: ['Jan.','Feb.','Mar.','Apr.','May.','Jun.','Jul.','Aug.','Sept.','Oct.','Nov.','Dec.'],
      iconData1: [
        {
          id: 1,
          icon: 'bilibili',
          color: 'black',
          url: 'https://www.bilibili.com'
        },
        {
          id: 2,
          icon: 'douyutv',
          color: 'black',
          url: 'https://www.douyu.com/directory/myFollow'
        },
        {
          id: 3,
          icon: 'movie',
          color: 'black',
          size: 450,
          url: 'http://gaoqing.la'
        },
        {
          id: 4,
          icon: 'taobao',
          color: '#fe5278',
          size: 480,
          url: 'https://www.taobao.com'
        },
      ],
      iconData2: [
        {
          id: 1,
          icon: 'aliyun',
          color: '#fe5278',
          url: 'https://www.aliyun.com'
        },
        {
          id: 2,
          icon: 'git',
          size: 450,
          color: '#fe5278',
          url: 'https://www.github.com'
        },
        {
          id: 3,
          icon: 'Vue',
          color: '#fe5278',
          url: 'https://cn.vuejs.org'
        },
        {
          id: 4,
          icon: 'Scriptchange',
          size: 450,
          color: '#fe5278',
          url: 'https://greasyfork.org/zh-CN/scripts'
        },
        {
          id: 5,
          icon: 'jingdong',
          size: 450,
          color: '#fe5278',
          url: 'https://www.jd.com'
        },
        {
          id: 6,
          icon: 'Shadowsocks-Logo',
          color: '#fe5278',
          url: 'https://ssready.io'
        },
        {
          id: 7,
          icon: 'zhihu',
          size: 470,
          color: '#fe5278',
          url: 'https://www.zhihu.com'
        },
        {
          id: 8,
          icon: 'fanyi',
          color: '#fe5278',
          size: 450,
          url: 'https://www.youdao.com'
        },
      ],
    }
  },
  methods: {
    handleScroll(){
      this.chinese = !this.chinese;
    },
    getTime() {
      let d = new Date()
      let YY = d.getFullYear(),
          mm = d.getMonth(),
          dd = d.getDate(),
          hh = d.getHours(),
          MM = d.getMinutes(),
          ss = d.getSeconds(),
          ww = d.getDay();

      this.YY = `${YY}`
      this.time = `${hh<10?'0':''}${hh}:${MM<10?'0':''}${MM}:${ss<10?'0':''}${ss}`
      if (this.chinese) {
        this.date = `${this.chineseMonths[mm]} ${dd}`
        this.weekDay = `${this.chineseWeeks[ww]}`
      } else {
        this.date = `${this.englishMonths[mm]} ${dd}`
        this.weekDay = `${this.englishWeeks[ww]}`
      }
    }
  },
  created() {
    this.getTime();
    window.setInterval(() => {
      this.getTime();
      this.clientHeight = document.documentElement.clientHeight;
      this.clientWidth = document.documentElement.clientWidth;
    }, 250);
  },
  mounted () {
    //监听鼠标滚动事件
    window.addEventListener('mousewheel', this.handleScroll, true)||window.addEventListener("DOMMouseScroll",this.handleScroll,false)
  },
};
</script>
<style>
.bg{
  background-image: url('./assets/background.png');
}
.black-font{
  font-family: sans-serif;
  color: black;
}
.pink-font{
  font-family: serif;
  color: #fe5278;
}
.v-enter-active{
  transition: all 1s ease;
}
.v-leave-active{
  transition: all 0s ease;
}
.v-enter,
.v-leave,
.v-leave-to{
  opacity: 0;
}
.v-enter-to{
  opacity: 1;
}
</style>
