<template>
  <div class="q-paper">
    <div class="q-progress">
        <div v-for="(topic,index) in topics" :class="[index<=inx?'active ':'','progress-bar']" :style="{display:'inline-block',width:100/topics.length+'%'}"></div>
    </div>
    <div class="q-page" :style="{width:topics.length*100+'%'}">
      <div class="q-topic" :style="{width:100/topics.length+'%',transform:'translate('+(-inx)*100+'%,0)'}" v-for="(topic,index) in topics">
        <div class="q-heading">{{topic.heading}}</div>
        <ul class="q-body">
          <li class="q-option" v-for="(option,index) in topic.body">
            {{option}}
          </li>
        </ul>

      </div>
    </div>
    <img class="q-action q-action-left " src="/static/images/left.svg" @click="goPrevious()">
    <img class="q-action q-action-right" src="/static/images/right.svg" @click="goNext()">
  </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        topics: [{
            heading: '标题一',
            body: ['选项一', '选项二', '选项三', '选项四']
          },
          {
            heading: '标题二',
            body: ['选项一', '选项二', '选项三', '选项四']
          },
          {
            heading: '标题三',
            body: ['选项一', '选项二', '选项三', '选项四']
          }
        ],
        inx: 0
      }
    },
    methods: {
      goPrevious: function () {
        if (this.inx === 0) {

        } else {
          this.inx--;
        }
      },
      goNext: function () {
        if (this.inx === this.topics.length - 1) {

        } else {
          this.inx++;
        }
      }
    }
  }

</script>

<style>
  ul {
    -webkit-padding-start: 0;
  }
  
  .q-paper {
    height: 100%;
    width: 100%;
    overflow-x: hidden;
  }
  
  .q-page {
    margin-top: 8rem;
  }
  
  .q-progress {
    position: absolute;
    height: 2.5rem;
    width: 100%;
    
  }
  .q-progress .progress-bar{
      background-color: yellowgreen;
      height: 100%;
      box-sizing: border-box;
      border-right: 1px solid #fff;
  }
  .q-progress .progress-bar:last-child{
      border-right:none;
  }
  .q-progress .progress-bar.active{
      background-color: lightseagreen;
  }
  .q-topic {
    display: inline-block;
    box-sizing: border-box;
    transition: transform 0.6s ease-out;
    padding: 0 5rem;
  }
  
  .q-heading {
    font-size: 2.5rem;
    margin-bottom: 5rem;
  }
  
  .q-body {
    margin-top: 1.5rem;
    list-style: none;
    font-size: 1.5rem;
  }
  
  .q-option {
    margin-top: 2.5rem;
  }
  
  .q-action {
    height: 5rem;
    display: block;
    position: absolute;
    top: 50%;
    transform: translate(0, -50%);
    cursor: pointer;
  }
  
  .q-action-left {
    left: 0;
  }
  
  .q-action-right {
    right: 0;
  }

</style>
