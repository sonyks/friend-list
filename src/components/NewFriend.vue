<template>
<form @submit.prevent="submitData">
    <div>
        <strong>Name</strong>
        <input type="text" v-model="enteredName" />
    </div>
    <div>
        <strong>Phone</strong>
        <input type="tel" v-model="enteredPhone" />
    </div>
    <div>
        <strong>E-Mail</strong>
        <input type="email" v-model="enteredEmail" />
    </div>
    <div>
        <button>Add Contact</button>
    </div>
</form>
</template>

<script>
export default {
    name: 'NewFriend',
    emits: ['add-contact'],
    data() {
        return {
            enteredName: '',
            enteredPhone: '',
            enteredEmail: ''
        };
    },
    methods: {
        submitData() {
            this.$emit('add-contact', this.enteredName, this.enteredPhone, this.enteredName);
        }
    }
}
</script>

<style scoped>
form {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 1rem auto;
    border-radius: 10px;
    padding: 1rem;
    text-align: center;
    width: 90%;
    max-width: 40rem;
}

input {
    font: inherit;
    padding: 0.15rem;
}

strong {
    font-weight: bold;
    margin-right: 1rem;
    width: 7rem;
    display: inline-block;
}

form div {
    margin: 1rem 0;
}
</style>
