<template>
    <header>
        <ul class="buttn">
            <li>clients</li>
            <li>orders</li>
            <li>messages</li>
            <li>users</li>
            <li>settings</li>
        </ul>
        <div class="user-info">
            <img class="avatar" src="../assets/avatar/user.jpg" />
            <p class="user-name">Jhon Doe</p>
            <img class="drop-btn" @click="openDropController ()" src="../assets/icons/down.svg" />
            <ul class="drop-menu" v-bind:class="{'active': isActive}">
                <li>setting</li>
                <li>exit</li>
            </ul>
        </div>
    </header>
</template>

<script>
export default {
  name: 'TheHeader',
  data: function () {
    return {
        isActive: false
    }
  },
  methods: {
    openDropController () {
		this.isActive = !this.isActive;
	}
  }
}
</script>
