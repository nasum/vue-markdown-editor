<template>
  <div id="app">
    <h1>Vue Markdown Editor</h1>
    <div class="editor-main">
      <div class="main">
        <text-area-with-emoji-suggest v-on:enter="setSource"></text-area-with-emoji-suggest>
        <div class="preview">
          <vue-markdown :source="source"></vue-markdown>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import VueMarkdown from 'vue-markdown'
  import TextAreaWithEmojiSuggest from './TextAreaWithEmojiSuggest.vue'
  export default {
    name: 'app',
    data () {
      return {
        source: ""
      }
    },
    methods: {
      setSource: function(data) {
        this.source = data
      }
    },
    components: {
      VueMarkdown,
      TextAreaWithEmojiSuggest
    }
  }
</script>

<style lang="scss">
  body {
    height: 100%;
  }
  #app{
    height: 100%;
    .editor-main{
      position: absolute;
      top: 100px;
      left: 0;
      right: 0;
      bottom: 0;
      .main{
        height: 100%;
        position: relative;
        .preview {
          box-sizing: border-box;
          position: absolute;
          right: 0;
          top: 0;
          width: 50%;
        }
      }
    }
  }
</style>
