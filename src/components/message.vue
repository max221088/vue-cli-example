<template>
    <!-- ref="message" :name="delName" -->
    <div class="message" v-bind:class="{active: isShow}">
        <div class="text-message">
            <div>Pokemon</div> 
            {{pokName}} 
            <div>have been removed</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TheMessage',
    data: function () {
        return {
            isShow: false,
            pokName: null,
        }
    },
    props: ['name'],
    methods: {
        sendMessage () {
            this.pokName = this.name.join(", ");
            this.isShow = true;
            setTimeout(() => this.isShow = false , 3000);
        }
    }
}
</script>
