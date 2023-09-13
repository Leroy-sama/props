<template>
    <li>
        <h2>{{ name }} {{ isFavourite ? '(favourite)' : '' }}</h2>
        <button @click="toggleDetails">Show detqails</button>
        <button @click="toggleFavourite">toggle favourite</button>
        <ul v-if="detailsVisible">
            <li><strong>Phone:</strong>{{ phoneNumber }}</li>
            <li><strong>Email:</strong>{{ emailAddress }}</li>
        </ul>
        <button @click="deleteFriend">Delete</button>
    </li>
</template>

<script>
    export default {
        // props: [
        // 'name',
        // 'phoneNumber',
        // 'emailAddress',
        // 'isFavourite'
        // ],
        props: { 
            id: {
                type: String,
                required: true
            },
            name: {
                type: String,
                required: true
            },
            phoneNumber: {
                type: String,
                required: true
            },
            emailAddress: {
                type: String,
                required: true
            },
            isFavourite: {
                type: Boolean,
                required: false, 
                default: false,
                // validator: function(value) {
                //     return value === '1' || value === '0'}
            }
        },
        emits: ['toggle-favourite', 'delete'],
        data() {
            return {
                detailsVisible: false,
            }
        },
        methods: {
            toggleDetails() {
                this.detailsVisible = !this.detailsVisible;
            },
            toggleFavourite() {
                this.$emit('toggle-favourite', this.id);
            },
            deleteFriend() {
                this.$emit('delete', this.id)
            }
        }
    }
</script>