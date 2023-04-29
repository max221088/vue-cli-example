<template>
    <div class="search">
        <div class="search-container">
            <img
                src="../assets/icons/search_icon.svg"
                class="search-icon"
            />
            <input type="text" v-model="filtQuery" @input="filterQuery()" 
            placeholder="Search for User,email,address..." class="input-search"/>'
            <img src="../assets/icons/filtering_icon.svg" class="search-icon"/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchPokemon',
    data: function () {
        return {
            filtQuery: null,
            filteredPokemon: []
        }
    },
    props: ['pokemon'],
    methods: {
        filterQuery: function() {
            let query = this.filtQuery.toLowerCase();
            this.filteredPokemon = this.pokemon.filter(function (el) {
				if (el.name.toLowerCase().indexOf(query) != -1) {
					return true;
				} else {
					return false;
				}
			});
            this.$emit('search-data', this.filteredPokemon);
        }
    },
}
</script>
