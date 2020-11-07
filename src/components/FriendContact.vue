<template>
<div>
    <h2>{{friend.name}}</h2>
    <button @click="toggleDetails">Show Details</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong> {{friend.phone}}</li>
        <li><strong>Email:</strong> {{friend.email}}</li>
    </ul>
    <button @click="deleteFriendMethod">Delete</button>
</div>
</template>

<script>
export default {
    name: 'FriendContact',
    props: {
        friend: {
            id: 'manuel',
            name: 'Manuel Lorenz',
            phone: '01234 5678 991',
            email: 'manuel@localhost.com'
        }
    },
    data() {
        return {
            detailsAreVisible: false
        }
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        deleteFriendMethod() {
            this.$emit('delete', this.friend.id);
        }
    }
}
</script>
