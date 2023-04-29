<template>
    <div class="modal-container" v-bind:class="{'active': isOpen}">
        <div class="overlay" @click="closeModal()">
            <div class="modal">
                <!-- inner JS -->
                <div class="spiner">
                    <div class="element"></div>
                    <div class="element"></div>
                    <div class="element"></div>
                    <div class="element"></div>
                    <div class="element"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ModalContainer',
  data: function () {
        return {
            isOpen: false,
            modalPok: [],
        }
    },
    props: ['rendModalData'],
    methods: {
        openModal () {
            this.isOpen = true;
            //console.log(this.rendModalData);
        },
        closeModal () {
            this.isOpen = false;
        },
    }
}
</script>
