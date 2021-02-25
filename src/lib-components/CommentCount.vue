<script>
import { defineComponent } from 'vue';
import { addScript, removeScript } from './helper';

export default /*#__PURE__*/defineComponent({
    name: 'CommentCount', // vue component name
    props: {
        websiteId:{type:String,required:true},
        mode:{type:String,default:'default'},
        id:{type:String,default: null}
    },
    methods: {
        setVariables(){
            if (this.websiteId) {
                window.HYVOR_TALK_WEBSITE = this.websiteId
            }
        }
    },
    mounted() {
        this.setVariables();
        var scriptId = 'ht-comment-count-script'
        if (document.getElementById(scriptId)) {
            removeScript(scriptId)
        }
        addScript('//talk.hyvor.com/web-api/count/', scriptId)
    }
});
</script>

<template>
    <span :data-talk-id="id" :data-talk-mode="mode" />
</template>