<template>
  <div>
    <span>{{ preConvertEmoji }}</span>
    <ul>
      <li v-for="key in suggest_filter()">
        {{ key }} : {{ emojiList[key] }}
      </li>
    </ul>
    <textarea class="editor" v-on:keyup="enter"></textarea>
  </div>
</template>

<script>
  import emojiOrigin from '../data/light.json'

  export default {
    name: 'suggest',
    data () {
      return {
        emojiList: emojiOrigin,
        preConvertEmoji: ""
      }
    },
    methods: {
      suggest_filter: function () {
        const emoji = this.preConvertEmoji.replace(/:/g, '')

        if (emoji == ""){
          return []
        }

        return Object.keys(emojiOrigin).filter(function (key) {
          return key.indexOf(emoji) == 0
        }).slice(0, 5)
      },
      enter: function(data){
        const words = data.target.value.split(/\s/)
        const lastWord = words.pop()
        if(lastWord.indexOf(':') == 0){
          this.preConvertEmoji = lastWord
        } else {
          this.preConvertEmoji = ""
        }

        this.$emit('enter', data.target.value)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .editor {
    box-sizing: border-box;
    height: 100%;
    left: 0;
    position: absolute;
    top: 25px;
    width: 50%;
  }
  ul{
    margin: 0;
    padding: 0;
    display: inline-block;
    li {
      display: inline-block;
    }
  }
</style>
