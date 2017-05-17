<template>
    <div class="child" v-bind:class="gender">
        <h3>{{ name }}</h3>
        <button @click="sendTodo">I need to pee</button>
    </div>
</template>

<script>
export default {
    name: 'child',
    props: ['name', 'gender'],
    methods: {
        sendTodo (){
            this.$emit('sendTodo', 'Bathroom duty', this.name + ' need to pee')
        }
    }
}
</script>

<style>

.child{
  padding: 20px;
  margin: 20px;
  background: silver;
}
.child.male{
  background: pink;
}
.child.female{
  background: lightblue;
}
</style>
