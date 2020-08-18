<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="/">HOPI</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <router-link class="nav-link"
                       :to="{
            name: 'home'
          }"
          >
            Home
          </router-link>
        </li>
        <template v-if="authenticated">
          <li class="nav-item">
            <router-link class="nav-link"
                :to="{
            name: 'dashboard'
          }"
            >
              Dashboard
            </router-link>
          </li>
          <li class="nav-link">
            {{ user.name }}
          </li>
          <li class="nav-link">
            <a href="#" @click.prevent="signOut">Sign Out</a>
          </li>
        </template>
        <template v-else>
          <li>
            <router-link class="nav-link"
                :to="{
            name: 'signin'
          }"
            >
              Sign In
            </router-link>
          </li>
        </template>
      </ul>
    </div>
  </nav>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'

export default {
  computed: {
    ...mapGetters({
      authenticated: 'auth/authenticated',
      user: 'auth/user',
    })
  },
  methods: {
    ...mapActions({
      signOutAction: 'auth/signOut'
    }),
    signOut() {
      this.signOutAction().then(() => {
        this.$router.replace({
          name: 'home'
        })
      })
    }
  }
}
</script>