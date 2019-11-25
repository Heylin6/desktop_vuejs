<template>
<div>
    <div class="span3" v-for="(item,index) in getbookmark.bookmarks" :key="index">
        <a :href="item.url" target="_BLANK">
            <div class="well box"
                :class="bookmarkColor(index+1)">
                <img src="assets/img/icons/box-1-white.png" alt="">
                <h3>{{ item.name }}</h3>
                <p>
                    {{ item.content }}
                </p>                
            </div>
        </a>
    </div>
 </div>   
</template>
<script>
export default {
    name  : 'ToolCard',
    props : ['getbookmark'],
    data() {
        return {
            
        }
    },
    methods: {
        bookmarkColor:function(index){
            let bmMode =index
            let rtNum = parseInt(bmMode % 7)
            let rtColor ='well-'
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
                    rtColor +=''
                    break
            }

            return rtColor
        },
    },
}
</script>