<template>
  <div class="sub-app">
    <!-- <template> -->
    <div>123</div>
    <div style="border: 1px solid #ccc">
      <Toolbar style="border-bottom: 1px solid #ccc" :editor="editorRef" :defaultConfig="toolbarConfig" :mode="mode" />
      <Editor style="height: 500px; overflow-y: hidden;" v-model="valueHtml" :defaultConfig="editorConfig" :mode="mode"
        @onCreated="handleCreated" />
    </div>
    <!-- </template> -->
  </div>
</template>

<script setup lang="ts">
import '@wangeditor/editor/dist/css/style.css' // 引入 css
import { ref, shallowRef, onMounted, onBeforeUnmount, nextTick } from 'vue';
import { Editor, Toolbar } from '@wangeditor/editor-for-vue'


const mode = 'default'
const editorRef = shallowRef()
// 内容 HTML
const valueHtml = ref('<p>hello</p>')
// 模拟 ajax 异步获取内容
onMounted(() => {
  // setTimeout(() => {
  nextTick(() => {
    valueHtml.value = '<p>模拟 Ajax 异步设置内容</p>'
  })

  // }, 1500)
})
const toolbarConfig = {}
const editorConfig = { placeholder: '请输入内容...' }

onBeforeUnmount(() => {
  const editor = editorRef.value
  if (editor == null) return
  editor.destroy()
})

const handleCreated = (editor) => {
  editorRef.value = editor // 记录 editor 实例，重要！
}
</script>

<style scoped>
.sub-app {
  width: 100%;
}
</style>
