<template>
  <mu-container>
    <mu-row justify-content="center">
      <mu-avatar :size="80">
        <div v-if="nickname == 'niabbf'">
          <img src="static/img/niabbf_head.jpg">
        </div>
        <div v-else-if="nickname == 'shifan'">
          <img src="static/img/shifan_head.jpg">
        </div>
        <div v-else>
          <img src="static/img/no_head.jpg">
        </div>
      </mu-avatar>
    </mu-row>
    <mu-row justify-content="center" class="margin-top-10">
      <div class="text-20">{{nickname}}</div>
    </mu-row>
    <mu-row justify-content="center" class="margin-top-10">
      <div class="text-10">
        您的信用等级:
        <span v-for="i in Math.floor(rate/2)">
          <mu-icon value=":iconfont icon-full-star" color="#ff8f00"></mu-icon>
        </span>
        <span v-if="rate % 2 === 1">
          <mu-icon value=":iconfont icon-half-star" color="#ffb300"></mu-icon>
        </span>
        <span v-for="i in Math.floor((10-rate)/2)">
          <mu-icon value=":iconfont icon-empty-star" color="#ffca28"></mu-icon>
        </span>
      </div>
    </mu-row>
    <mu-list class="margin-top-20">
      <mylist icon=":iconfont icon-history" content="历史清单" color="#2196f3" to="history"></mylist>
      <div class="divider"></div>
      <mylist icon=":iconfont icon-notice" content="系统消息" color="#00bcd4"></mylist>
      <div class="divider-large"></div>
      <mylist icon=":iconfont icon-setting" content="个人设置" color="#607d8b"></mylist>
    </mu-list>
  </mu-container>
</template>

<script>

import {getRate, getNickname} from '@/static/localStorage'

export default {
  name: 'individual',
  data () {
    return {
      nickname: getNickname(),
      rate: Number(getRate())
    }
  }
};
</script>

<style scoped>
.text-10 {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 10px;
}
.text-20 {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 20px;
}
.margin-top-10 {
  margin-top: 10px;
}
.margin-top-20 {
  margin-top: 20px;
}
.divider {
  height: 5px;
}
.divider-large {
  height: 30px;
}
</style>
