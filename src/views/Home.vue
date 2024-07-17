<template>
  <div class="page-content">
    <h1 class="title">QR Code Сканнер</h1>
    <div class="page-description">
      Для получения документации воспользуйтесь одним из способов:
    </div>
    <div class="scanner-container">
      <div class="scanner-wrapper">
        <h3>Загрузить файл c QR-кодом</h3>
        <qr-capture @decode="onDecode" class="scanner"></qr-capture>
      </div>
      <div class="scanner-wrapper">
        <div class="handInputTitle"><h3>Ввести номер ТУ</h3></div>
        <div class="handInput">
          <input class="tuInput" placeholder="Введите номер ТУ" />
          <button class="tuInputButton">Отправить</button>
        </div>
      </div>
    </div>
    <div v-if="data" class="result">
      <h2>Результат сканирования:</h2>
      <a :href="data" target="_blank">{{ data }}</a>
    </div>
    <div class="handInputWrapper">
      <h3>Сканировать онлайн</h3>
      <qr-stream @decode="onDecode" class="scanner">
        <div class="frame"></div>
      </qr-stream>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { QrCapture, QrStream } from "vue3-qr-reader";

const data = ref(null);

function onDecode(decodedData) {
  data.value = decodedData;
}
</script>

<style scoped>
.page-content {
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem;
  font-family: "Roboto", Arial, sans-serif;
  color: #333;
}

.title {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 2.5rem;
}

.page-description {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 1.1rem;
}

.scanner-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 2rem;
  margin-bottom: 2rem;
}

.scanner-wrapper {
  flex: 1;
  min-width: 300px;
  max-width: 450px;
  background-color: #ffffff;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.scanner {
  width: 100%;
  overflow: hidden;
}

.frame {
  border: 2px solid var(--maincolor);
  position: absolute;
  top: 20%;
  left: 20%;
  width: 60%;
  height: 60%;
  border-radius: 8px;
}

.handInputWrapper {
  margin-bottom: 2rem;
  text-align: center;
}

h3 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.handInput {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.tuInput {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

.tuInputButton {
  padding: 0.5rem 1rem;
  background-color: var(--maincolor);
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

.tuInputButton:hover {
  background-color: var(--maincolor);
}

.result {
  background-color: #e9ecef;
  padding: 1.5rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.result h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

.result a {
  color: var(--maincolor);
  text-decoration: none;
  word-break: break-all;
  font-weight: bold;
}

.result a:hover {
  text-decoration: underline;
}

.scanner-wrapper {
  background-color: #f8f9fa;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}
.scanner-wrapper {
  border: 1px solid var(--maincolor);
}
</style>
