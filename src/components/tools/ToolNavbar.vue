<template>
        <div>
            <nav>
              <ul class="nav topnav">
                <li v-for="(item) in getclassname.classnames" 
                   :key="item.id"
                   :class="[bookmarkColor(item),{'active':item.code === getcodestr}]"
                    class="dropdown">
                  <a href="#" @click.prevent="[setcodestr(item),setbmtabcolor(item)]">
                      <i class="icon-white"
                        :class="bookmarkIcon(item)">
                      </i> 
                      {{ item.name }}
                  </a>
                </li>
              </ul>
            </nav>
        </div>
</template>
<script>
export default {
    name  : 'ToolNavbar',
    props : ['getclassname','getcodestr'],
    data(){
        return {

        }
    },
    methods: {
        bookmarkColor:function(item){
            let bmMode =item.cid
            let rtNum = parseInt(bmMode % 7)
            let rtColor =''
            switch(rtNum)
            {
                case 1 :
                    rtColor ='danger'
                    break
                case 2 :
                    rtColor ='orange'
                    break
                case 3 :
                    rtColor ='warning'
                    break
                case 4 :
                    rtColor ='success'
                    break
                case 5 :
                    rtColor ='primary'
                    break
                case 6 :
                    rtColor ='lndigo'
                    break
                case 0 :
                    rtColor ='info'
                    break                                                                                                                   
                default:                    
                    rtColor =''
                    break
            }
            return rtColor
        },
        bookmarkIcon:function(item){
            let bmMode =item.cid
            let rtNum = parseInt(bmMode % 7)
            let rtIcon =''
            switch(rtNum)
            {
                case 1 :
                    rtIcon ='icon-home'
                    break
                case 2 :
                    rtIcon ='icon-star'
                    break
                case 3 :
                    rtIcon ='icon-leaf'
                    break
                case 4 :
                    rtIcon ='icon-signal'
                    break
                case 5 :
                    rtIcon ='icon-film'
                    break
                case 6 :
                    rtIcon ='icon-heart'
                    break
                case 0 :
                    rtIcon ='icon-glass'
                    break                                                                                                                   
                default:                    
                    rtIcon =''
                    break
            }
            return rtIcon
        },
        setcodestr(item){
            //丟資料回給老爸
            //給老爸時的名稱叫postPid
            this.$emit('tabChange',item);
        },
        setbmtabcolor(item){
            this.$emit('bmcolortabChange',item);
        }
    },
    computed: {

    }
}
</script>