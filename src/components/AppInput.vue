<template>
    <div class="form-control" :class="{invalid: error}">
        <label :for="id">{{ label }}</label>
        <input type="text" id="name" :placeholder="placeholder" :value="modelValue" @input="change">
        <small v-if="error">{{ error }}</small>
      </div>
</template>

<script>
export default {
    name: 'AppInput',
    data(){
        return{
            id: 'input' + Math.random()
        }
    },
    props:{
        label: String,
        error: String,
        placeholder: String,
        modelValue: String
    },
    emits: ['update:modelValue'],
    methods:{
        change(event){
            this.$emit('update:modelValue', event.target.value)
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
