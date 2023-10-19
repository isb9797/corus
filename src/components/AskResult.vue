<script setup lang="js">
  import {ref, onMounted} from "vue";


  let ask = ref([]);

  let msg = ref(null);

  const removeData = () => {
      localStorage.removeItem('ask');
      ask.value = [];
      msg.value = "Данные опроса удалены";
  }

  onMounted(() => {
      if (localStorage.getItem('ask')) {
          try {
              ask.value = JSON.parse(localStorage.getItem('ask'));

          } catch (e) {
              localStorage.removeItem('ask');


          }

      } else {
          msg.value = "Данные опроса не найдены";

      }
  })

</script>

<template>
  <div class="ask-form__finaly">
      <h2>Результаты опроса</h2>

      <div v-if="msg === null">
          <div  class="ask-form__results" v-for="result in ask">
              {{result}}


          </div>

          <button type="button" @click="removeData" class="remove" >Удалить данные</button>
      </div>

      <div v-else>
          <div  class="ask-form__results">
              {{msg}}


          </div>
      </div>



  </div>
</template>

<style scoped lang="sass">

.ask-form
  &__finaly
    display: block
    background-color: #f2f2f2
    padding: 20px
    h2
      margin-bottom: 20px
  &__results
    margin-bottom: 10px
    font-size: 18px

.remove
  margin-top: 40px
  display: flex
  align-items: center
  justify-content: center
  color: #ffffff
  background: #000
  padding: 15px 50px
  border-radius: 100px
  cursor: pointer
  border: none

</style>
