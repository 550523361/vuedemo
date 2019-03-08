<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
<template>
  <div class="paperContainer" id="printTest" style="width:210mm;border: 1px solid #f0a;position: relative;">
    <div>
      <!--<span style="width: 30px;display: inline-block;border: 0px solid #00f;word-break: break-all;writing-mode:tb-rl;text-align: left;padding-right: 85px;">
          <span class="route180Deg">____________</span>
          <span class="route180Deg">:</span>
          <span class="route90Deg">名</span>
          <span class="route90Deg">姓</span>
          <span class="route180Deg">____________</span>
          <span class="route180Deg">:</span>
          <span class="route90Deg">号</span>
          <span class="route90Deg">学</span>

          <span class="route180Deg">____________</span>
          <span class="route180Deg">:</span>
          <span class="route90Deg">级</span>
          <span class="route90Deg">班</span>
          <span class="route180Deg">____________</span>
          <span class="route180Deg">:</span>
          <span class="route90Deg">级</span>
          <span class="route90Deg">年</span>

      </span>-->
      <span>
              <img src="http://img-steward-test.goodaa.com.cn/61a17727ecbc4ffea404d37868c02c5b.png" style="margin-right: 50px;" alt="">
          </span>
    </div>
    <div >
      <div v-for="(item,seq) in itemList" :key="seq+'_'+item.value" class="itemContainer">
        <span style="position: relative;">{{seq+1}}、</span><span>{{item.name}}</span><span :ref="'point_'+seq" class="pointSpan" style="position: relative;"><span >(</span><span style="position: absolute;display: inline-block;">{{points[seq].left}}、{{points[seq].top}}</span><span>)</span></span>
      </div>
      <button @click="getPoints">获取坐标</button>
      <button @click="doPrint" style="display: inline-block;padding: 10px 15px;">打印</button>
    </div>
  </div>
</template>

<script>
    import  _ from 'underscore'
    export default {
        name: 'index',
        components:{
        },
        data () {
            return {
                itemList:[
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                    {
                        name:'低调许久的李小璐晒生活家居照，还是那么美，大长腿太撩人了',
                        value:2
                    },
                    {
                        name:'国航航班紧急备降俄罗斯！空姐大吼：别拿东西，跑！',
                        value:21
                    },
                    {
                        name:'三大运营商回应政府工作报告：坚决贯彻提速降费和携号转网要求',
                        value:2111
                    },
                    {
                        name:'3月5日，国务院总理李克强在作政府工作报告时提出，“今年中小企业宽带平均资费再降低15%，移动网络流量平均资费再降低20%以上，在全国实行‘携号转网’，规范套餐设置，使降费实实在在、消费者明明白白。”',
                        value:211
                    },
                ],
                points:[{"left":549,"top":0},{"left":493,"top":32},{"left":563,"top":64},{"left":170,"top":160},{"left":549,"top":192},{"left":493,"top":224},{"left":563,"top":256},{"left":170,"top":352},{"left":549,"top":384},{"left":501,"top":416},{"left":571,"top":448},{"left":170,"top":544},{"left":557,"top":576},{"left":501,"top":608},{"left":571,"top":640},{"left":170,"top":736},{"left":557,"top":768},{"left":501,"top":800},{"left":571,"top":832},{"left":170,"top":928},{"left":557,"top":960},{"left":501,"top":992},{"left":571,"top":1024},{"left":170,"top":1120}]
            }
        },
        methods:{
            getPoints(){
                console.log(this.$refs)
                let points=Object.values(this.$refs);
                points=_.flatten(points)
                console.log("points",points)

                let pointsArray=[];
                points.forEach(item=>{
                    console.log(item.offsetLeft,item.offsetTop)
                    pointsArray.push({left:item.offsetLeft,top:item.offsetTop})
                })

                console.log(JSON.stringify(_.sortBy(pointsArray,item=>item.top)))
            },
            doPrint() {
                $(".centerContainer").print();
                //window.document.body.innerHTML=bdhtml; // 最后还原页面
            }
        },
        created(){
        }
    }
</script>
<style>

  .itemContainer{
    font-size: 14px;
    line-height: 32px;
    text-align: left;
  }
  .pointSpan{
    display: inline-block;
    width: 80px;
    position: relative;
    text-align: left;
    margin-left: 15px;
  }
  .pointSpan span:nth-child(3){
    position: absolute;
    right: 0px;
  }
  .paperContainer{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: stretch;
    width: 100%;
    height: 100%;
  }
  .paperContainer>div:first-child{
    width: 120px;
    border: 0px solid #faa;
    flex-grow: 0;
    flex-shrink: 0;
    align-self: center;
    text-align: right;

  }
  .paperContainer>div:last-child{
    border: 0px solid #faa;
    flex-grow: 1;
    flex-shrink:1;
  }
  .route90Deg{
    display: inline-block;
    transform: rotateZ(-90deg)
  }
  .route180Deg{
    display: inline-block;
    transform: rotateZ(-180deg)
  }
</style>

<!-- Add "scoped" attribute to limit CSS to this component only -->
