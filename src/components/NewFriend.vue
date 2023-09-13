<template>
    <form action="/" @submit.prevent="submitData">
        <div>
            <label for="name">Name</label>
            <input type="text" v-model="enteredName">
        </div>
        <div>
            <label for="email">Email</label>
            <input type="email" v-model="enteredEmail">
        </div> 
        <div>
            <label for="phone">Phone</label>
            <input type="tel" v-model="enteredPhone">
        </div>
        <div>
            <button>Add contact</button>
        </div>
    </form>
</template>

<script>
    export default {
        emits: ['add-contact'],
        data() {
            return {
                enteredName: '',
                enteredEmail: '',
                enteredPhone: ''
            }
        },
        methods: {
            submitData () {
                this.$emit('add-contact', 
                this.enteredName, 
                this.enteredEmail, 
                this.enteredPhone
                )
            }
        }
    }
</script>