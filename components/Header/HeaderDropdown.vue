<template>
      <b-nav-item-dropdown right no-caret>
        <template slot="button-content">
          <img src="~static/img/avatars/10.png" class="img-avatar">
        </template>
        <b-dropdown-header tag="div" class="text-center"><strong>Perfil</strong></b-dropdown-header>
        <b-dropdown-item to="/perfil"><i class="fa fa-user"></i>Editar</b-dropdown-item>
        <b-dropdown-item @click="logout"><i class="fa fa-lock"></i> Logout</b-dropdown-item>
      </b-nav-item-dropdown>
</template>

<script>
  export default {
    name: 'header-dropdown',
    methods: {
      async logout() {
        try {
          this.$store.dispatch('logout').then(() => {
            this.$router.push('/login')
          })
        } catch (e) {
          this.formError = e.message
        }
      }
    }
  }
</script>

