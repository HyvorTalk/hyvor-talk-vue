<script>
import { defineComponent } from 'vue';
import { addScript, removeScript } from './helper';

export default /*#__PURE__*/defineComponent({
  name: 'Embed', // vue component name
  props: {
    websiteId:{type:String,required:true},
    url:{type:String,default: false},
    id:{type:String,default: false},
    title:{type:String,default:document.title},
    loadMode:{type:String,default:'default'},
    language:{type:String,default:null},
    sso:{type:String,default:null},
    palette:{type:Object,default:null},
    authorEmail:{type:String,default:null},
  },
  methods: {
    setVariables(){
      window.HYVOR_TALK_WEBSITE = this.websiteId,
      window.HYVOR_TALK_CONFIG = {
        url:this.url,
        id: this.id,
        title: this.title,
        loadMode: this.loadMode,
        language: this.language,
        sso: this.sso,
        palette: this.palette,
        authorEmail:this.authorEmail
      }
    },
    checkScript() {
        if (document.getElementById('ht-embed-script')) {
            removeScript('ht-embed-script')
        }
        addScript('//talk.hyvor.com/web-api/embed', 'ht-embed-script')
    }
  },
  mounted() {
      this.setVariables();
      this.checkScript();
  }
});
</script>

<template>
  <div id='hyvor-talk-view'></div>
</template>
