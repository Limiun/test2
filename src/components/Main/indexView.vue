<template>
    <el-container>
      <el-header id="nav-fixed" :class="{nav_fixed : isFixed}">
        <el-menu :default-active="this.$route.path" class="el-menu-demo" mode="horizontal" @select="handleSelect" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
          <el-menu-item index="1"><router-link  to="/writeBlog" >首页</router-link></el-menu-item>
          <el-submenu index="2">
            <template slot="title">我的工作台</template>
            <router-link  to="/testView1" ><el-menu-item index="2-1">技术博客</el-menu-item></router-link>
            <router-link  to="/testView2"> <el-menu-item index="2-2">项    目</el-menu-item></router-link>
            <router-link  to="/testView2"> <el-menu-item index="2-2">辣鸡仓库</el-menu-item></router-link>
<!--            <el-menu-item index="2-3">选项3</el-menu-item>-->
<!--            <el-submenu index="2-4">-->
<!--              <template slot="title">选项4</template>-->
<!--              <el-menu-item index="2-4-1">选项1</el-menu-item>-->
<!--              <el-menu-item index="2-4-2">选项2</el-menu-item>-->
<!--              <el-menu-item index="2-4-3">选项3</el-menu-item>-->
<!--            </el-submenu>-->
          </el-submenu>
          <el-menu-item index="3" disabled>消息中心</el-menu-item>
          <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>

          <el-submenu index="5">
            <template slot="title">嘤嘤嘤</template>
            <router-link  to="/dailyDoubts" ><el-menu-item index="5-1">每日疑惑</el-menu-item></router-link>
            <router-link  to="/testView2"> <el-menu-item index="5-2">每日解惑</el-menu-item></router-link>
            <router-link  to="/testView2"> <el-menu-item index="5-3">每年的需要做的小事</el-menu-item></router-link>
            <!--            <el-menu-item index="2-3">选项3</el-menu-item>-->
            <!--            <el-submenu index="2-4">-->
            <!--              <template slot="title">选项4</template>-->
            <!--              <el-menu-item index="2-4-1">选项1</el-menu-item>-->
            <!--              <el-menu-item index="2-4-2">选项2</el-menu-item>-->
            <!--              <el-menu-item index="2-4-3">选项3</el-menu-item>-->
            <!--            </el-submenu>-->
          </el-submenu>

          <el-row class="button">
            <el-button icon="el-icon-search" circle></el-button>
            <router-link  to="/writeBlog" ><el-button type="primary" icon="el-icon-edit" circle></el-button></router-link>
            <el-button type="success" icon="el-icon-check" circle></el-button>
            <el-button type="info" icon="el-icon-message" circle></el-button>
            <el-button type="warning" icon="el-icon-star-off" circle></el-button>
            <el-button type="danger" icon="el-icon-delete" circle></el-button>
          </el-row>
        </el-menu>
      </el-header>
      <div style="margin-top: 50px">
        <el-container>

          <el-main class="el-main" >

            <div class="navbar">
              <!-- 路由匹配到的组件将显示在这里 -->
              <router-view></router-view>
            </div>
          </el-main>
          <el-aside width="200px">Aside</el-aside>
        </el-container>
        <el-footer>
          <div class="block">
            <span class="demonstration">默认 Hover 指示器触发</span>
            <el-carousel height="150px">
              <el-carousel-item v-for="item in 4" :key="item">
                <h3 class="small">{{ item }}</h3>
              </el-carousel-item>
            </el-carousel>
          </div>
        </el-footer>

      </div>


    </el-container>
</template>

<script>
    export default {
        name: "indexView",
      data(){
          return{
            isFixed:false,
            offsetTop:0,
            height:{
              height:'',
            }
          };
      },
      mounted(){
        // 设置bar浮动阈值为 #fixedBar 至页面顶部的距离
        this.offsetTop = document.querySelector('#nav-fixed').offsetTop;
        // 开启滚动监听
        window.addEventListener('scroll', this.handleScroll);
      },
      created(){
          this.hh()
      },
      methods:{
        // 滚动监听  滚动触发的效果写在这里
        handleScroll() {
          var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
          if (scrollTop >= this.offsetTop) {
            this.isFixed = true;
          } else {
            this.isFixed = false;
          }
        },
        hh(){
          this.height.height = window.innerHeight-200+'px';
          console.log("hhh:"+this.height.height)
        }
      },
      destroyed() {
          window.removeEventListener('scroll',this.handleScroll)
      }
    }
</script>
<style>


  .el-header:nth-child(1) {
    position: fixed;
    z-index: 2;
    top: 0;
    width: 100%;
  }
  .el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 150px;
    margin: 0;
  }


  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }

  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  /*.el-container:nth-child(5) .el-aside,*/
  /*.el-container:nth-child(6) .el-aside {*/
  /*  line-height: 260px;*/
  /*}*/

  .button{
    float: right;
    position: relative;/*脱离文档流*/
    margin-top: 10px;
    margin-right: 10px;
    border: 0px ;


  }
  .el-main {
    height:calc(70vh)
  }


  #nav-fixed{
    height: 71px;
  }
  /*.el-container el-main {*/
  /*  height: 722px;*/
  /*}*/
</style>
