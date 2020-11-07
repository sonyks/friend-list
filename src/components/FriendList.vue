<template>
<div>
    <section id="app">
        <NewFriend @add-contact="addContact"></NewFriend>
        <ul>
            <li v-for="friend in friends" :key="friend.id">
                <FriendContact :friend="friend" @delete="deleteContact" />
            </li>
        </ul>
    </section>
</div>
</template>

<script>
import FriendContact from './FriendContact'
import NewFriend from './NewFriend'

export default {
    name: 'FriendList',
    props: {
        msg: String
    },
    components: {
        FriendContact,
        NewFriend
    },
    data() {
        return {
            friends: [{
                    id: 'manuel',
                    name: 'Manuel Lorenz',
                    phone: '01234 5678 991',
                    email: 'manuel@localhost.com'
                },
                {
                    id: 'julie',
                    name: 'Julie Jones',
                    phone: '09876 543 221',
                    email: 'julie@localhost.com'
                }
            ]
        }
    },
    methods: {
        addContact(name, phone, email) {
            const newFriendContact = {
                id: new Date().toISOString(),
                name,
                phone,
                email
            };
            this.friends.push(newFriendContact);
        },
        deleteContact(id) {
            this.friends = this.friends.filter(friend => friend.id !== id);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
* {
    box-sizing: border-box;
}

html {
    font-family: 'Jost', sans-serif;
}

body {
    margin: 0;
}

header {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 3rem auto;
    border-radius: 10px;
    padding: 1rem;
    background-color: #58004d;
    color: white;
    text-align: center;
    width: 90%;
    max-width: 40rem;
}
</style>
