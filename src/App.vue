<template>
  <div id="wysivue">
    <ckeditor :editor="editor" v-model="value" :config="editorConfig"></ckeditor>
  </div>
</template>

<script>
import CKEditor from '@ckeditor/ckeditor5-vue2'
import ClassicEditor from '@ckeditor/ckeditor5-build-classic'
export default {
  name: 'Wysivue',
  data () {
    return {
      editor: ClassicEditor,
      value: '',
      editorConfig: {
        toolbar: {
          items: [
            'heading',
            'bold',
            'italic',
            'link',
            'BulletedList',
            'NumberedList',
            'undo',
            'redo'
          ]
        }
      }
    }
  },
  mounted () {
    this.value = this.html
  },
  props: {
    html: String
  },
  components: {
    ckeditor: CKEditor.component
  },
  watch: {
    value: function (value) {
      this.$emit('change', value)
    },
    html: function () {
      this.value = this.html
    }
  }
}
</script>

<style>
</style>
