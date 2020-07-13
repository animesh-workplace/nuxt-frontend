<template>
  <div>
    <template>
        <b-navbar>
            <template slot="brand">
                <b-navbar-item tag="router-link" :to="{ path: '/' }">
                    <img
                        src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
                        alt="Lightweight UI components for Vue.js based on Bulma"
                    >
                </b-navbar-item>
            </template>
            <template slot="start">
                <b-navbar-item href="#">
                    Home
                </b-navbar-item>
                <b-navbar-item href="#">
                    Documentation
                </b-navbar-item>
                <b-navbar-dropdown label="Info">
                    <b-navbar-item href="#">
                        About
                    </b-navbar-item>
                    <b-navbar-item href="#">
                        Contact
                    </b-navbar-item>
                </b-navbar-dropdown>
            </template>

            <template slot="end">
                <b-navbar-item tag="div">
                    <div class="buttons">
                      <div v-if="$auth.loggedIn">
                        <b-button tag="router-link"
                            type="is-primary">
                            Username
                        </b-button>    

                        <b-button tag="router-link"
                            type="is-danger">
                            Logout
                        </b-button>                                             
                      </div>

                      <div v-else>
                        <b-button tag="router-link"
                            to="/login"
                            type="is-primary">
                            Login
                        </b-button>    

                        <b-button tag="router-link"
                            to="/register"
                            type="is-danger">
                            Register
                        </b-button>                     
                      </div>
                    </div>
                </b-navbar-item>
            </template>

        </b-navbar>
    </template>

    <section class="main-content columns">
      <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">
          General
        </p>
        <ul class="menu-list">
          <li
            v-for="(item, key) of items"
            :key="key"
          >
            <nuxt-link
              :to="item.to"
              exact-active-class="is-active"
            >
              <b-icon :icon="item.icon" /> {{ item.title }}
            </nuxt-link>
          </li>
        </ul>
      </aside>

      <div class="container column is-10">
        <nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' }
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' }
        }
      ]
    }
  }
};
</script>

<style>
  html {
    overflow-y: auto;
  }
</style>
