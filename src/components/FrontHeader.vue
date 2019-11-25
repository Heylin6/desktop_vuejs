<template>
    <div class="navbar navbar-fixed-top">
      <div class="navbar-inner">
        <div class="container">
          <!-- logo -->
          <a class="brand logo" href="index.html">
            <img src="assets/img/logo.png" alt="">
          </a>
          <!-- end logo -->

          <!-- top menu -->
          <navbar :getclassname="getclassname" 
                  :getcodestr="getcodestr" 
                  @tabChange="setcodeStr"
                  @bmcolortabChange="setbmtabcolor"/>
          <!-- end menu -->
        </div>
      </div>
    </div>
</template>
<script>
import navbar from './tools/ToolNavbar'

export default {
  name  : 'ToolNavbar',
  props : ['getcodestr','getclassname'],
  components:{
    navbar
  },
  data(){
    return{
     
    }
  },
  methods: {
    getFilterCode(){
        var vm=this
       
    },
    setcodeStr(item){
        this.$emit('tabChange',item);
    },
    setbmtabcolor(item){
        this.$emit('bmcolortabChange',item);        
    }
  },
  created() {
      
  },
}
</script>
