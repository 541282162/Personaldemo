<template>
  <div class="app">

    <!--轮播图-->
    <div class="container1">
      <el-row>
        <el-col :lg="14">
          <img :src="showInfo.imgSrc">
        </el-col>
        <el-col :offset="1" :lg="9">
          <div style="height: 420px">
            <div style="width: 80%;text-align: center;">
              <h3 style="font-family: Arial;font-size: 15px">{{showInfo.dairy}}</h3>
              <h1>{{showInfo.title}}</h1>
              <p>{{showInfo.content}}</p>
            </div>

            <div style="position: absolute;bottom:0;">
              <el-button-group style="float: left;margin-left: 15px;margin-bottom: 10px">
                <el-button icon="el-icon-arrow-left" @click="prevShowInfo"></el-button>
                <el-button icon="el-icon-arrow-right " @click="nextShowInfo"></el-button>
              </el-button-group>
              <p style="margin-left: 400px;margin-bottom: 0px">{{showInfo.id}}/{{showInfo.total}}</p>
            </div>

          </div>
        </el-col>
      </el-row>

    </div>

    <!--日记展示-->
    <div class="container2">
      <el-row>

        <!--左侧-->
        <el-col :offset="1" :lg="14" :sm="22" :xs="22">
          <!--主作品展示栏-->
          <div style="text-align: center;">
            <img :src="img1" style="height: 350px">
            <h3 style="font-family: Arial;font-size: 15px">{{mainShow.time}}</h3>
            <h1>{{mainShow.title}}</h1>
            <p>{{mainShow.intro}}</p>
            <el-divider style="color: honeydew"></el-divider>
          </div>
          <!--作品展示-->
          <div style="margin-top:100px ">
            <el-row>
              <el-col :offset="2" :lg="10" :sm="10" :xs="10"
                      style="margin-bottom: 40px"
                      v-for="item in showList"
                      :key="item.id">
                <img :src="item.imgSrc">
                <h3>{{item.time}}</h3>
                <h2>{{item.title}}</h2>
                <p>{{item.content}}</p>
              </el-col>
            </el-row>
          </div>
        </el-col>

        <!--右侧-->
        <el-col :offset="1" :lg="7" :sm="20" :xs="20">
          <!--个人介绍栏-->
          <div>

            <p style="color: white;margin-bottom: 60px;font-size: 20px;background-color: black;height: 35px"><b>关 于 我</b></p>

            <div class="block">
              <el-avatar :size="200" :src="img2"></el-avatar>
            </div>
            <p>　年轻的你只如云影掠过

              　　而你微笑的面容极浅极淡

              　　逐渐隐没在日落后的群岚

              　　遂翻开那发黄的扉页

              　　命运将它装订得极为拙劣

              　　含着泪我一读再读

              　　却不得不承认

              　　青春是一本太仓促的书</p>
            <p style="color: white;margin-top: 60px;font-size: 20px;background-color: black;height: 35px"><b>关 于 我</b></p>


          </div>
          <!--日记记录-->
          <div v-for="item in blogList" :key="item.id" >
            <el-row>
              <el-col :lg="8" :sm="8" :xs="8" style="margin-top: 15px">
                <img :src="item.img" style="height: 120px" >
              </el-col>
              <el-col :offset="1" :lg="15" :sm="14" :xs="14" style="text-align: left">
                <div style="height: 120px"  >
                  <p>{{item.content}}</p>
                  <p><i>小甘</i></p>
                </div>
              </el-col>
            </el-row>
          </div>

          <!--图片与标签-->
          <div style="margin-top: 40px">
            <img :src="img3">
            <div style="margin-top: 50px">
              <el-tag v-for="item in tags" :key="item.label" style="margin:10px ">{{item.label}}</el-tag>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Index1",
    data() {
      return {
        timer1: '',
        value: 0,
        author: '冰心',
        screenWidth: document.body.clientWidth,
        img1:require("../assets/images/img4.jpg"),
        img2:require("../assets/images/img18.jpg"),
        img3:require("../assets/images/img19.jpg"),
        mainShow:{
          id:'1',
          time:'2020 / 10 /6',
          title:'《死后》',
          intro:'我死后 墓地要种满樱花。\n' +
            '   杂草 应该把荒凉的范围扩大，\n' +
            '\n' +
            '  我的墓碑将翻越人世，遍布锋芒\n' +
            '   但不失浪漫 陪伴我的乌鸦要百里挑一，\n' +
            '  尽量选取贵族后裔\n' +
            ' 在我的墓地上 有野心的风，熟悉政治的漩涡 \n' +
            '              有经验的枫叶，委身于霜，\n' +
            '            大器晚成在旧山河里一路走红。我的后世对手将习惯性仰望\n' +
            '           在我不为人知的生前身后，我的寂寞已脱亚入欧 在我不盖国旗的孤寂中，'
        },
        tags:[
          {label:'体育'},
          {label:'健康'},
          {label:'美食'},
          {label:'小吃'},
          {label:'梦想'},
          {label:'蓝莓'},
          {label:'小瀑布'},
        ],
        showInfo: {
          id: 1,
          imgSrc: require("../assets/images/img1.jpg"),
          dairy: '2020 /10 /4',
          title: '索玛丽与森林之神',
          content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
          , total: 3
        },
        blogList:[{
          id:1,
          img:require("../assets/images/img11.jpg"),
          content:'要努力呀！为了想要的生活，为了人间的烟火气，为了今天的风和月！'
        },{   id:2,
          img:require("../assets/images/img12.jpg"),
          content:'要努力呀！为了想要的生活，为了人间的烟火气，为了今天的风和月！'

        },{   id:3,
          img:require("../assets/images/img13.jpg"),
          content:'要努力呀！为了想要的生活，为了人间的烟火气，为了今天的风和月！'
        },{   id:4,
          img:require("../assets/images/img15.jpg"),
          content:'要努力呀！为了想要的生活，为了人间的烟火气，为了今天的风和月！'
        }],

        imgList: [{
          id: 1,
          imgSrc: require("../assets/images/img1.jpg"),
          dairy: '2020 /10 /4',
          title: '索玛丽与森林之神',
          content: '刚才在森林里受伤的索玛丽，露出了和你一样的表情，脸部肌肉扭曲，眼球也变得湿润。' +
            '看到那种表情，我的思维就陷入了混乱。最主要是，这里（心）静不下来。'
        }, {
          id: 2,
          imgSrc: require("../assets/images/img2.jpg"),
          dairy: '2020 /12 /5',
          title: '索玛丽与森林之神',
          content: '我已经活了998年253天，再过1年112天我的生命活动就会停止'
        }, {
          id: 3,
          imgSrc: require("../assets/images/img3.jpg"),
          dairy: '2020 /12 /5',
          title: '索玛丽与森林之神',
          content: '索玛丽：“爸爸”'+'\n'+'森林之神：“索玛丽 你没事吧！”'
            +'\n'+'索玛丽："索玛丽一点事都没有，但是 爸爸是不是有事 看起来好疼 都是我的错 对不起"'
        }

        ],
        showList: [{
          id: 1,
          imgSrc: require("../assets/images/img5.jpg"),
          time: '2020 /10 /4',
          title: '索玛丽与森林之神',
          content: '刚才在森林里受伤的索玛丽，露出了和你一样的表情，脸部肌肉扭曲，眼球也变得湿润。'
          ,
        },
          {
            id: 2,
            imgSrc: require("../assets/images/img6.jpg"),
            time: '2020 /10 /4',
            title: '青衫烟雨客，似是故人来。',
            content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
            ,
          }, {
            id: 3,
            imgSrc: require("../assets/images/img7.jpg"),
            time: '2020 /10 /4',
            title: '索玛丽与森林之神',
            content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
            ,
          },
          {
            id: 4,
            imgSrc: require("../assets/images/img8.jpg"),
            time: '2020 /10 /4',
            title: '青衫烟雨客，似是故人来。',
            content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
            ,
          }, {
            id: 5,
            imgSrc: require("../assets/images/img9.jpg"),
            time: '2020 /10 /4',
            title: '索玛丽与森林之神',
            content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
            ,
          },
          {
            id: 6,
            imgSrc: require("../assets/images/img10.jpg"),
            time: '2020 /10 /4',
            title: '青衫烟雨客，似是故人来。',
            content: '你说帘外海棠，锦屏鸳鸯，后来庭院春深，咫尺画堂。你说笛声如诉，费尽思量，后来茶烟尚绿，人影茫茫'
            ,
          }]
      }
    },

    mounted() {//定时运行轮播图下一张
      this.timer1 = setInterval(this.nextShowInfo, 5000)

    },
    methods: {
      nextShowInfo() {//轮播图，下一个
        // this.value++
        // console.log("this.value");
        if (this.showInfo.id === this.showInfo.total) {
          let i = 1
          this.showInfo.id = i
          this.showInfo.imgSrc = this.imgList[i - 1].imgSrc
          this.showInfo.dairy = this.imgList[i - 1].dairy
          this.showInfo.title = this.imgList[i - 1].title
          this.showInfo.content = this.imgList[i - 1].content
        } else {
          let i = this.showInfo.id
          i = i + 1
          this.showInfo.id = i
          this.showInfo.imgSrc = this.imgList[i - 1].imgSrc
          this.showInfo.dairy = this.imgList[i - 1].dairy
          this.showInfo.title = this.imgList[i - 1].title
          this.showInfo.content = this.imgList[i - 1].content
        }
      },
      prevShowInfo() {//轮播图，上一个
        console.log("prev");
        if (this.showInfo.id === 1) {
          let i = 3
          this.showInfo.id = i
          this.showInfo.imgSrc = this.imgList[i - 1].imgSrc
          this.showInfo.dairy = this.imgList[i - 1].dairy
          this.showInfo.title = this.imgList[i - 1].title
          this.showInfo.content = this.imgList[i - 1].content
        } else {
          let i = this.showInfo.id
          i = i - 1
          this.showInfo.id = i
          this.showInfo.imgSrc = this.imgList[i - 1].imgSrc
          this.showInfo.dairy = this.imgList[i - 1].dairy
          this.showInfo.title = this.imgList[i - 1].title
          this.showInfo.content = this.imgList[i - 1].content
        }
      },

    },

  }

</script>

<style scoped>
  .container1 {
    position: relative;
    margin-top: 50px;
    height: 400px;
  }


  .container2 {
    position: relative;
    margin-top: 80px;
  }

  .container1 img {
    width: 100%;
    height: 400px;
  }

  .container2 img {
    width: 100%;
    height: 170px;
  }
  h3{
    color: #00BBFF;
  }
  p{
    font-size: 15px;
  }
</style>
