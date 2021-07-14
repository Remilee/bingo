<template>
  <q-page class="main row ">
    <div class="main-content column">
      <h2 class="title"> Вечерне-пятничное бинго! </h2>
      <table class="table-container">
        <tbody v-html="row">
        </tbody>
      </table>
    </div>
  </q-page>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  components: { /* ExampleComponent */ },
  setup() {
    const values = [
      'Когда офис в СПБ?',
      'Правки по новостному отчету',
      'Кто-то уходит в отпуск',
      'Когда лицензии?',
      'Хранилка упала',
      'Рассылка не работает',
      'Мы молодцы!',
      'Правки по эффективности поиска',
      'Теле2 просит посчитать строчки кода',
      'Как погода в Москве?',
      'ПСИ',
      'Заполните Джиру',
      '"А ну включаем камеры!"',
      'Three hundred bucks',
      '"Ну все, давай, пока"',
      '**Звуки дрели**',
      'Дима пьёт чай',
      '"Жени нет, кто начнет?"',
    ];
    const arrayValues = values.sort(() => Math.random() - 0.5);
    const cellsOnRow = [6, 12];
    const rowCell = [];
    rowCell.push('<tr>');
    arrayValues.forEach((item, index) => {
      if (cellsOnRow.includes(index)) {
        rowCell.push('<tr>');
      }
      const tempCell = `<td class="cellClass"> ${item.toString()} </td>`;
      rowCell.push(tempCell);
      if (cellsOnRow.includes(index + 1)) {
        rowCell.push('</tr>');
      }
    });
    rowCell.push('<tr>');
    const row = rowCell.join('');
    return {
      arrayValues,
      row
    };
  },
});
</script>

<style lang="sass">
.main
  background: linear-gradient(90deg, #3AACFF 9.63%, #347CD1 100%)
  font-family: "Montserrat", Arial, sans-serif !important
.main-content
  margin: auto
  padding: 0

.title
  color: white
  align-self: center

.table-container
  background-color: white
  border-collapse: collapse

  .cellClass
    width: 18em
    height: 10em
    padding: 2em
    text-align: center
    border: 2px solid #2F80ED
    font-weight: 500

    &:hover
      background-color: #a9cdff
      transition: 0.5s
      cursor: pointer

</style>
