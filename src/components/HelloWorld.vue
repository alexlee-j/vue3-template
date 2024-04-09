<script setup lang="ts">
import { ref, onMounted } from 'vue'
import JsBarcode from 'jsbarcode'

defineProps<{ msg: string }>()

const count = ref(0)

onMounted(() => {
  JsBarcode("#barcode")
  .options({font: "OCR-B"}) // Will affect all barcodes
  .CODE128("2p8up8uyh7", {fontSize: 18, textMargin: 0})
  .blank(20) // Create space between the barcodes
  .render();
})
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  <canvas id="barcode" width="335px" height="183px"></canvas>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
#barcode {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
