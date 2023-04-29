<template>
    <main>
        <table class="user-table">
            <thead>
                <tr>
                    <td>
                        <img
                            src="../assets/icons/button_minus_icon.svg"
                            class="icon-select-user"
                        />
                    </td>
                    <td>
                        <span class="select-user">
                            2 user selected
                        </span>
                    </td>
                </tr>
                <tr>
                    <td><button @click="delElementController()">Delete</button></td>
                    <td>Foto</td>
                    <td>Id</td>
                    <td>Name</td>
                    <td>Base Experiense</td>
                    <td>Ability</td>
                    <td>Type Name</td>
                    <td>Weight</td>
                    <td>Height</td>
                </tr>
            </thead>
            <tbody>
                <!-- inner JS -->
                <tr v-for="(item, index) in renderData" :key="index">
                    <td><input type ="checkbox" :data-index="index" class= "checkbox"></td>
                    <!-- <td><button :data-index="index" @click="delElementController">O</button></td> -->
                    <td><img :data-name="item.name" class="front-pokemon" :src="item.sprites.front_default"></td>
                    <td>{{item.id}}</td>
                    <td class="poke-name">{{item.name}}</td>
                    <td>{{item.base_experience}}</td>
                    <td>{{item.abilities[0].ability.name}}</td>
                    <td>{{item.types[0].type.name}}</td>
                    <td>{{item.weight}}</td>
                    <td>{{item.height}}</td>
                </tr>
            </tbody>
        </table>
        <!-- <message ref="message" :name="delName"></message> -->
    </main>
</template>

<script>
export default {
    name: 'TheMain',
    data: function () {
    return {
        pokemon: [],
        renderData: [],
        delName: [],
        delPokemon: [],
        API: "https://pokeapi.co/api/v2/pokemon/",
    }
  },
    methods: {
        openDropController () {
            this.isActive = !this.isActive;
        },
        searchData: function (data) {
            this.renderData = data;
        },
        delElementController () {
            let checkboxes = document.querySelectorAll('.checkbox');
            for (let i = checkboxes.length - 1; i >= 0; i--) {
                if (checkboxes[i].checked) {
                    let delIndex = checkboxes[i].dataset.index;
                    this.delPokemon = this.renderData.splice(delIndex, 1);
                    this.delName.push(this.delPokemon[0].name);
                    checkboxes[i].checked = false;
                }
            }
        this.$refs.message.sendMessage();
        this.pokemon = this.renderData;
        this.delName = [];
        }
        
    },
    created: function () {
        if (localStorage.getItem('pokemon') == null) {
            fetch(this.API)
            .then(function (response) {
            return response.json();
        })
            .then(function (data) {
                let pok = data.results;
                let pokList = [];
                pok.forEach(function (el) {
                    fetch(el.url)
                    .then(function (response) {
                        return response.json();
                    })
                    .then(function (data){
                        pokList.push(data);
                        if (pokList.length == pok.length) {
                            localStorage.setItem("pokemon", JSON.stringify(pokList));
                            this.renderData = JSON.parse(localStorage.getItem("pokemon"));
                        }				
                    }.bind(this));
                }.bind(this));
            }.bind(this));
        }
        this.renderData = JSON.parse(localStorage.getItem("pokemon"));
        this.pokemon = this.renderData;
    }
}
</script>
