<template>
  <div :style="TodoStylesDiv">
    <input type="checkbox" v-model="isChecked">
    <p :style="isChecked ? TextCheckboxStyleChecked : TextCheckboxStyle">{{ title }}</p>
  </div>
</template>

<script>
export default {
    name: "TodoCard",
    props: ['title'],
    data(){
        return{
            isChecked: false,
            TodoStylesDiv: {
                display: 'flex',
                justifyContent: 'center'
            },
            TextCheckboxStyle: {
                color: '#d35400',
                fontSize: '20px',
                marginLeft: '5px',
                fontWeight: 700,
                fontFamily: 'cursive'
            },
            TextCheckboxStyleChecked: {
                color: '#27ae60',
                fontSize: '20px',
                marginLeft: '5px',
                fontWeight: 700,
                fontFamily: 'cursive'
            }
        }
    }
}
</script>

<style>

</style>