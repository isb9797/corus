<script setup lang="js">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
import { ref, onMounted, onBeforeMount } from 'vue';
import axios from "axios";


let d = ref(null);




  onMounted(() => {
    fetch('https://jsonplaceholder.typicode.com/todos')
        .then(response => response.json())
        .then(json => {

          json = json.slice(1,5);
          console.log(json);
          d.value = json;
        });



  })





// new Vue({
//   el: '#ask-form',
//   data() {
//     return {
//       info: null
//     };
//   },
//   mounted() {
//     axios
//         .get('https://api.coindesk.com/v1/bpi/currentprice.json')
//         .then(response => (this.info = response));
//   }

</script>

<template>
  <div class="ask-form" id="ask-form">
    <div class="ask-form__header">
      <span class="ask-form__header-title">Опросы</span>
      <a href="#" class="ask-form__header-all">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="21" viewBox="0 0 20 21" fill="none">
          <g clip-path="url(#clip0_82_1751)">
            <path fill-rule="evenodd" clip-rule="evenodd" d="M18.75 3C18.75 2.66848 18.6183 2.35054 18.3839 2.11612C18.1495 1.8817 17.8315 1.75 17.5 1.75H2.5C2.16848 1.75 1.85054 1.8817 1.61612 2.11612C1.3817 2.35054 1.25 2.66848 1.25 3V18C1.25 18.3315 1.3817 18.6495 1.61612 18.8839C1.85054 19.1183 2.16848 19.25 2.5 19.25H17.5C17.8315 19.25 18.1495 19.1183 18.3839 18.8839C18.6183 18.6495 18.75 18.3315 18.75 18V3ZM0 3C0 2.33696 0.263392 1.70107 0.732233 1.23223C1.20107 0.763392 1.83696 0.5 2.5 0.5L17.5 0.5C18.163 0.5 18.7989 0.763392 19.2678 1.23223C19.7366 1.70107 20 2.33696 20 3V18C20 18.663 19.7366 19.2989 19.2678 19.7678C18.7989 20.2366 18.163 20.5 17.5 20.5H2.5C1.83696 20.5 1.20107 20.2366 0.732233 19.7678C0.263392 19.2989 0 18.663 0 18V3ZM5.625 9.875C5.45924 9.875 5.30027 9.94085 5.18306 10.0581C5.06585 10.1753 5 10.3342 5 10.5C5 10.6658 5.06585 10.8247 5.18306 10.9419C5.30027 11.0592 5.45924 11.125 5.625 11.125H12.8663L10.1825 13.8075C10.1244 13.8656 10.0783 13.9346 10.0468 14.0105C10.0154 14.0864 9.99921 14.1678 9.99921 14.25C9.99921 14.3322 10.0154 14.4136 10.0468 14.4895C10.0783 14.5654 10.1244 14.6344 10.1825 14.6925C10.2406 14.7506 10.3096 14.7967 10.3855 14.8282C10.4614 14.8596 10.5428 14.8758 10.625 14.8758C10.7072 14.8758 10.7886 14.8596 10.8645 14.8282C10.9404 14.7967 11.0094 14.7506 11.0675 14.6925L14.8175 10.9425C14.8757 10.8844 14.9219 10.8155 14.9534 10.7395C14.9849 10.6636 15.0011 10.5822 15.0011 10.5C15.0011 10.4178 14.9849 10.3364 14.9534 10.2605C14.9219 10.1845 14.8757 10.1156 14.8175 10.0575L11.0675 6.3075C11.0094 6.24939 10.9404 6.20329 10.8645 6.17185C10.7886 6.1404 10.7072 6.12421 10.625 6.12421C10.5428 6.12421 10.4614 6.1404 10.3855 6.17185C10.3096 6.20329 10.2406 6.24939 10.1825 6.3075C10.1244 6.36561 10.0783 6.4346 10.0468 6.51052C10.0154 6.58644 9.99921 6.66782 9.99921 6.75C9.99921 6.83218 10.0154 6.91356 10.0468 6.98948C10.0783 7.0654 10.1244 7.13439 10.1825 7.1925L12.8663 9.875H5.625Z" fill="black"/>
          </g>
          <defs>
            <clipPath id="clip0_82_1751">
              <rect width="20" height="20" fill="white" transform="translate(0 0.5)"/>
            </clipPath>
          </defs>
        </svg>

        Все опросы
      </a>
    </div>

    <h3 class="ask-form__title">
      В каком формате работают подразделения бэк-офиса?
    </h3>

<!--    Сами инпуты тоже можно поместить в отдельные компоненты-->
    <form action="#">
      <div class="checkbox-control" v-for="ask in d">

        <input type="checkbox" :name=ask.id :id=ask.id>
        <label :for=ask.id>{{ask.title}}</label>
      </div>




      <div class="ask-form__footer">
        <button class="ask-form__submit">Голосовать</button>
        <span class="ask-form__results">Проголосовало: <b>16</b></span>
      </div>

    </form>

  </div>
</template>

<style scoped lang="sass">
$bgColor: #f5f4f4

.ask-form
  display: flex
  flex-direction: column
  width: 100%
  min-height: 720px
  background: $bgColor
  padding: 30px
  background-image: url("assets/ask-form/ask-bg.png")
  background-repeat: no-repeat
  background-position: bottom right

  .checkbox-control
    margin-bottom: 30px
    input
      display: none
      &:checked+label:before
        content: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAACXBIWXMAAAsTAAALEwEAmpwYAAAAgElEQVR4nO2SuwmAQBAFRzCUiwwNrcPoCrCLzcxs0TYMjM3EUEQ4QQR/eAsi9wqYWd4+CPlrMiDSglfABJSa8AZIfMNlAzcB/s1aaqAF8odrMXcvKoAR6C4k1ZtaFslwIhEfnR9JxOdD9xLRWIt1P+k1p2idRAW+JgViLXgI6pkBrdIq3SW1qBgAAAAASUVORK5CYII=")

    label
      display: flex
      gap: 20px
      align-items: center
      &:before
        content: ""
        background: #fff
        width: 24px
        height: 24px
        display: flex
        justify-content: center
        align-items: center
        cursor: pointer
        //content: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAACXBIWXMAAAsTAAALEwEAmpwYAAAAgElEQVR4nO2SuwmAQBAFRzCUiwwNrcPoCrCLzcxs0TYMjM3EUEQ4QQR/eAsi9wqYWd4+CPlrMiDSglfABJSa8AZIfMNlAzcB/s1aaqAF8odrMXcvKoAR6C4k1ZtaFslwIhEfnR9JxOdD9xLRWIt1P+k1p2idRAW+JgViLXgI6pkBrdIq3SW1qBgAAAAASUVORK5CYII=")
        border-radius: 4px
        

  &__header
    display: flex
    align-items: center
    gap: 40px

    &-title
      font-size: 28px
      font-weight: 500

    &-all
      display: flex
      align-items: center
      gap: 10px
      font-size: 13px
      text-decoration: none
      color: #000
      font-weight: 500

      svg
        width: 20px
        height: 20px

  &__title

    margin: 24px 0 17px 0
    padding-left: 20px
    border-left: 4px solid #000
    display: flex
    align-items: center
    font-size: 26px

    min-height: 117px

  &__footer
    margin-top: 30px
    width: 100%
    display: flex
    gap: 20px
    align-items: center

  &__submit
    display: flex
    align-items: center
    justify-content: center
    color: #ffffff
    background: #000
    padding: 15px 50px
    border-radius: 100px
    cursor: pointer

</style>
