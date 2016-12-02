<template>
  <div id="app">
    <h1>Vue Markdown Editor</h1>
    <div class="editor-main">
      <div class="main">
        <textarea class="editor" v-on:keyup="enter"></textarea>
        <div class="preview">
          <vue-markdown :source="source"></vue-markdown>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import VueMarkdown from '../../../src/VueMarkdown' // development
import VueMarkdown from 'vue-markdown' // production
export default {
  name: 'app',
  data () {
    return {
      source: ""
    }
  },
  methods: {
    enter: function(data){
      this.source = data.target.value
    }
  },
  components: {
    VueMarkdown
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
        .editor {
          box-sizing: border-box;
          height: 100%;
          left: 0;
          position: absolute;
          top: 0;
          width: 50%;
        }
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
