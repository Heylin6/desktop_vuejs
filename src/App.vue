<template>
  <div id="app">
    <header id="header">
        <Header :getcodestr="code" 
                :getclassname="classnamelist" 
                @tabChange="setcodeStr"
                @bmcolortabChange="setbmtabcolor"/>
    </header>
    
    <section id="intro">
    </section> 
    <section id="maincontent">
        <Container :getcodestr="code"
                   :getbookmark="BookMarkInit"
                   :gettabcontent="tab_content"
                   :getbmktabcolor="bmktabcolor"/>
    </section> 
    <!-- <router-view/> -->
  </div>
</template>
<script>
import Header from './components/FrontHeader.vue'
import Container from './components/FrontContainer.vue'
import classname from './json/classname.json';
import bookmarkObj from './json/bookmark.json';
export default {
  components:{
    Header,Container
  },
  data() {
    return {
      code:'all',
      classnamelist:{},
      bookmarklist:{},
      temp_bookmarklist:{},
      tab_content:{
          name:'所有書籤',
          content:'未分類都集中放這'
      },
      bmktabcolor:'btn-danger'
    }
  },
  methods: {
    getClassName(){
        var vm=this
        vm.classnamelist = classname
        //console.log('vm.classnamelist',vm.classnamelist);
    },
    getBookMark(){
        var vm=this
        vm.bookmarklist = bookmarkObj
        vm.temp_bookmarklist= bookmarkObj
        //console.log('vm.bookmarklist',vm.bookmarklist);
    },
    setcodeStr(item){
      var vm=this
      vm.code = item.code
    },
    setbmtabcolor(item){
      var vm=this
      let bmMode = item.cid
      let rtNum = parseInt(bmMode % 7)
      let rtColor = 'btn-'

      switch(rtNum)
      {
                case 1 :
                    rtColor +='danger'
                    break
                case 2 :
                    rtColor +='orange'
                    break
                case 3 :
                    rtColor +='warning'
                    break
                case 4 :
                    rtColor +='success'
                    break
                case 5 :
                    rtColor +='primary'
                    break
                case 6 :
                    rtColor +='lndigo'
                    break
                case 0 :
                    rtColor +='info'
                    break                                                                                                                   
                default:                    
                    rtColor =''
                    break
      }
      console.log(rtColor)
      console.log(item)
      vm.tab_content = item
      vm.bmktabcolor = rtColor
    }
  },
  created() {
    this.getClassName()
    this.getBookMark()    
  },
  computed: {
    BookMarkInit(){
        var vm=this
        if(vm.code === 'all'){
            /* 不可使用 vm.temp_bookmarklist = vm.bookmarklist 這樣兩個會變一樣 */
            /* 要用 Object.assign 來複製原先的 */
            vm.temp_bookmarklist = Object.assign({},vm.bookmarklist)
            return vm.temp_bookmarklist
        }
        else{
            /* 不可使用 vm.temp_bookmarklist = vm.bookmarklist 這樣兩個會變一樣 */
            /* 要用 Object.assign 來複製原先的 */
            vm.temp_bookmarklist = Object.assign({},vm.bookmarklist)
            vm.temp_bookmarklist.bookmarks = vm.temp_bookmarklist.bookmarks.filter(item => item.code === vm.code)
            return vm.temp_bookmarklist
        }
    }
  },
}
</script>
<style>
@import 'assets/css/bootstrap-responsive.css';
@import 'assets/css/bootstrap.css';
@import 'assets/css/docs.css';
@import 'assets/css/style.css';
@import 'assets/color/success.css';


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} 
</style>
