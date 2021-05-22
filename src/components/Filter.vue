<!--
|---------------------------------------------
| Filter Component 
|---------------------------------------------
| @usage Import the component and use 
| <Filter :optionsSelect="array_json" nameSelect="name_of_select"/>
-->

<template>
    <select v-model="value" :name="name" class="select-personal mr-sm-2" :id="id">
        <option v-for="option in options" :key="option.id" :value="option.id">
            {{option.value}}
        </option>
    </select>
</template>

<script>

export default {
    name: 'Filter',
    props: {
        nameSelect: String,
        optionsSelect: Array,
        idSelect: String
    },
    data (){
        return {
            options: this.optionsSelect,
            name: this.nameSelect,
            id: this.idSelect,
            value: 1
        }
    }
}
</script>

<style scoped>

</style>