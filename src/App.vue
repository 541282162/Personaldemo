<template>

  <div>
    <div
      style="position: fixed;top:0;
      left:0;
      width:100%;z-index: 200;
      background-color: white;
      box-shadow: 0 0 15px rgba(0,0,0,0.15)">


      <el-row>
        <div v-model="ifShow" v-if="ifShow==0">
          <el-button style="float: right"
                     @click="drawer1=true"
                     v-model="direction"
                     label="ltr"><i class="el-icon-s-fold"></i></el-button>
        </div>
        <!--title-->

        <el-col :lg="4" :sm="4" :xs="4" class="nikki">
          <span >小甘</span>
        </el-col>

        <div v-model="ifShow" v-if="ifShow== 1">
          <el-col :lg="12" :sm="12" :xs="4">
            <el-menu :default-active="this.$route.path"
                     router
                     class="el-menu-mode"
                     mode="horizontal"
                     @close="handleClose"
                     text-color="#00BBFF"
                     active-text-color="#ffd04b">
              <el-menu-item  v-for="item in list" :key="item.id" :index="item.url" >{{item.label}}</el-menu-item>
            </el-menu>
          </el-col>


          <!--搜索-->
          <el-col :lg="4" :sm="4" :xs="4">
            <el-input suffix-icon="el-icon-search"
                      placeholder="搜索"
                      class="search"
                      v-model="searchData"></el-input>
          </el-col>

          <!--联系方式-->
          <el-col :lg="3" :sm="3" :xs="3" :offset="1">
            <el-tooltip
              v-for="item in emailList"
              :key="item.id"
              :content="item.content"
              style="margin-left: 20px;margin-top: 20px ">
              <i :class="item.icon"></i>
            </el-tooltip>
          </el-col>
        </div>
      </el-row>
    </div>
    <!--      <div ><el-button @click="getData"></el-button></div>-->

    <!--抽屉-->
    <div>
      <el-drawer
        :visible.sync="drawer1"
        :direction="direction"
        style="width:900px">

        <el-menu :default-active="this.$route.path"
                 router
                 class="el-menu-vertical-demo"
                 text-color="00BBFF"
                 active-text-color="#ffd04b">
          <el-menu-item  v-for="item in list" :key="item.id" :index="item.url" >{{item.label}}</el-menu-item>
        </el-menu>
        <el-input suffix-icon="el-icon-search"
                  placeholder="Search and hit enter..." class="search"
                  style="float: left">
        </el-input>
      </el-drawer>
    </div>
    <router-view></router-view>
  </div>


</template>

<script>


  export default {
    name: "App",
    mounted() {
      this.timer=setInterval(this.getWidth,300)
    },

    data() {
      return {
        a: "",
        ifShow: 1,
        drawer1: false,
        direction: "ltr",
        timer:'',
        searchData:'',
        emailList:[{
          id:'1',
          content:'QQ邮箱',
          icon:'el-icon-s-custom'
        },{
          id:'2',
          content:'电话号码',
          icon:'el-icon-phone'
        },{
          id:'3',
          content:'微信',
          icon:'el-icon-s-promotion'
        }],
        list:[{
          id:1,
          label:'首页',
          order:1,
          url:'/components/index'
        },{
          id:2,
          label:'个人作品',
          order:2,
          url:'/components/personWorks'
        },{
          id:3,
          label:'个人文章',
          order:3,
          url:'/components/personArticle'
        },{
          id:4,
          label:'个人简历',
          order:4,
          url:'/components/personResume'
        },{
          id:5,
          label:'用户反馈',
          order:5,
          url:'/components/userFeedback'
        }]
      }
    },

    methods: {
      handleClose(key,keyPath){
        console.log(key,keyPath)
      },
      getWidth(){
        const that = document.body.clientWidth

        if (that <= 992) {
          this.ifShow = 0
          // this.$forceUpdate
          //console.log("ifShow:" + this.ifShow)
        } else {
          this.ifShow = 1
          // this.$forceUpdate
          // console.log("ifShow:" + this.ifShow)
        }
        // console.log(that)
        //  console.log("整体" + this.ifShow)
      }

    }

  }
</script>

<style scoped>

  .nikki {
    font-size: 20px;
    margin-top: 15px;
    font-family: Calibri;
  }

  .search {
    height: 14px;
    width: 200px;
    margin-left: 50px;
    font-size: 12px;
    margin-top: 10px;
    text-align: center;
  }

  .el-menu-mode {
    border-bottom: none;
  }

  .end {
    width: 120px;
    margin-top: 25px;
    margin-left: 39px;
  }

</style>
