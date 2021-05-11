<template>
    <Modal @close="$emit('close')"
           title="Second modal with form">
        <template v-slot:body>
            <form @submit.prevent>
                <label>Name:</label>
                <input type="text">
                <label>Email:</label>
                <input type="email">
                <button type="submit">Отправить</button>
            </form>
        </template>
    </Modal>
</template>

<script>
    import Modal from "./Modal";

    export default {
        name: "ModalValidate",
        components: {
            Modal
        }
    }
</script>

<style scoped>

</style>