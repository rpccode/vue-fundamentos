<template>
    <h2>{{ customTitle }}</h2>
    <p> {{ counter }}  <sup>2</sup> = {{ SquareCounter }}</p>
    <div>
            <button v-on:click="incrementCount">+1</button>
            <button v-on:click="decrementCount">-1</button>
        </div>
</template>

<script> 
    export default {
        props:{
            title:String,
            start:{
                type: Number,
                required: true,
                default:1,
                validator(value){
                    return value > 0;
                }
            }
        },
        data() {
            return {
                counter: this.start,
            }
        },
        methods: {
            getSquareValue(){
                return this.counter * this.counter
            },
            incrementCount(){
                this.counter++;
            },
            decrementCount(){
    this.counter--;
            }
        },
        computed:{
            SquareCounter(){
                return this.counter * this.counter
            },
            customTitle({title}){
                // console.log(title)
                return this.title || 'counter'
            }
        }
    }
</script>

<style >
    button{
        background-color: #41B883;
        border-radius: 5px;
        border:1px solid white;
        color:white;
        cursor: pointer;
        margin: 0 25px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;
    }
    button:hover{
        background-color: #5aa67b;
    transition: 0.3s ease-in-out;
    }
</style>