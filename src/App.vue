<template>
  <div class="container">
    <form class="card"
          @submit.prevent="submitForm"  
    >
      <h1>Анкета на Vue разработчика!</h1>
      
      <app-input :error="errors.name" placeholder="Введите имя" label="Как тебя зовут?" v-model="name"></app-input>

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input type="number" id="age" v-model.number="age">
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="kgd">Калининград</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input type="radio" name="trip" value="yes" v-model="relocate"/> Да</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="trip" value="no" v-model="relocate"/> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox" name="vuex" value="vuex" v-model="skills"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" name="cli" value="cli" v-model="skills"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" name="router" value="router" v-model="skills"/> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Согласие</span>
        <div class="checkbox">
          <label><input type="checkbox" name="agree" value="agree" v-model="agree">Согласен</label>
        </div>
      </div>

      <button type="submit"  class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import AppInput from "./components/AppInput.vue"

export default {
  components:{
    AppInput
  },
  data(){
    return{
      name: '',
      age: 23,
      city: 'kgd',
      relocate: null,
      skills: [],
      agree: false,
      errors: {
        name: null,
      }
      
    }
  },
  methods:{
    formValid(){
      let valid = true;

      if (this.name.length == 0){
        this.errors.name = "Имя не может быть пустым";
        valid = false;
      } else {
        this.errors.name = null;
      }

      return valid;
    },
    submitForm(){
      if (this.formValid()){
        console.group("Form data");
        console.log('Name', this.name.replace(/ +/g, ' '));
        console.log('Age', this.age);
        console.log('City', this.city);
        console.log('Relocate', this.relocate);
        console.log('Skills', this.skills);
        console.log('Agree', this.agree);
        console.groupEnd();
      }
    }
  }
}

</script>

<style>
    small{
      color: brown;
    }
    .form-control.invalid input {
      border-color: brown;
    }
</style>
