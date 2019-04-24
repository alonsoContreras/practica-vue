<template>
  <div>
        <form class="Form" @submit.prevent="onSubmit">
            <input type="text" placeholder="Teclee lo que desea buscar" class="FormInput"
                v-model="searchText" v-validate="{required: true, min:5}" name="val1"/>            
            <button type="submit" class="FormButton"> Buscar Giphy </button>            
        </form>
    </div>  
</template>
<script>
export default {
    name: "SearchForm",
    data () {
        return {
            searchText: '',
        }
    },
    methods: {
        onSubmit () {
            this.$validator.validate().then(valid => {
                if (valid) {
                   /* const newSearch = {
                        preview_gif: this.searchImage,
                    }; */
                    this.$emit('val1', this.searchText);
                    this.searchText = '';
                }
            });
        }
    }
}
</script>
<style scoped>
.Form {
    width: 500px;
    margin: auto;
    margin-top: 1rem;
    border: 1px solid;
    padding: 1rem 0;
    border-radius: 5px;
    background-color: white;
    box-shadow: 5px 4px 0px rgba(132, 131, 131, 0.75);
}
 .FormInput {
     height: 15px;
     width: 80%;
     border: 1px solid  rgba(132, 131, 131, 0.75);;
     border-radius: 5px;
     margin-bottom: 1rem;
     padding: 0.5rem;
 }
 .FormButton {
     background-color: #42b983;
     color: white;
     border: none;
     width: 100px;
     height: 60px;
     border-radius: 5px;
 }
 .FormButton:hover {
     background-color: orange;
 }
</style>

