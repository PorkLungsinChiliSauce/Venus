<template>
  <div id="app">
    <div id="theme-wrapper">
      <vheader></vheader>
      <div id="page-wrapper" class="container">
        <div class="row">
          <vmenu></vmenu>
          <div id="content-wrapper">
            <div class="row">
              <div class="row">
                <div class="col-lg-12">
                  <div id="content-header" class="clearfix">
                    <ol class="breadcrumb">
                      <li><a href="#">首页</a></li>
                      <li class="active"><span>{{menuText}}</span></li>
                    </ol>
                    <h1>Gallery</h1>
                  </div>

                </div>
              </div>
              <div class="col-lg-12">
                  <router-view></router-view>
              </div>
            </div>
            <vfooter></vfooter>
          </div>
        </div>
      </div>
    </div>
    <configtool></configtool>
  </div>
</template>
<script>
  import configtool from './../components/config-tool.vue'
  import vheader from './../components/v-header.vue'
  import vmenu from './../components/v-menu.vue'
  import vfooter from './../components/v-footer.vue'
  import init from './../js/common/init'

  export default {
    name: 'app',
    components: {
      configtool,
      vheader,
      vmenu,
      vfooter
    },
    data(){
     return{
       menuText:""
     }
    },
    mounted: function () {
      this.$nextTick(function () {
        new init();
      })
      window.bus.$on('change', function (id) {
        this.menuText=id;
      })
    }
  }
</script>
