<template>
    <div class="container">
            <div class="row">
                <div class="span3">
                    <h3 class="heading-success">
                        <span class="btn btn-large" :class="getbmktabcolor">
                            <i class="m-icon-big-swapright m-icon-white"></i>
                        </span>
                        &nbsp;&nbsp;{{gettabcontent.name}}
                    </h3>
                <p>{{gettabcontent.content}}</p>
                </div>
                    <BookMarkCard :getbookmark="getbookmark"/>
            </div>
    </div>
</template>
<script>
import BookMarkCard from './tools/ToolCard'

export default {
    name  : 'FrontContainer',
    props : ['getcodestr','getbookmark','getbmktabcolor','gettabcontent'],
    components:{
        BookMarkCard
    }
}
</script>