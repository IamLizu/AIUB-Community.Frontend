<template>
  <div>
    <v-app toolbar v-if="fontsLoaded">
      <navbar></navbar>
      <main>
        <v-content>
          <transition name="slide-fade"  mode="out-in">
            <router-view></router-view>
          </transition>
          <download class="pa-0"></download>
          <signIn class="pa-0"></signIn>
          <signUp class="pa-0"></signUp>
        </v-content>
      </main>    
      <v-footer class="footer pa-2">
        <code>>> Website under development stage. More features coming up! <a target="_blank" href="https://google.com"><img class="footer-pic" height="20px" src="/static/GitHub-Mark-32px.png" alt="Github"></a></code>
      </v-footer>
    </v-app>
    <div class="wait-screen" v-else><div></div><div></div><div></div></div>
  </div>
</template>

<script>
  import navbar from '@/components/helpers/NavBar'
  import download from '@/components/helpers/Download'
  import signIn from '@/components/helpers/SignIn'
  import signUp from '@/components/helpers/SignUp'
  export default {
    components: {
      navbar,
      download,
      signIn,
      signUp
    },
    computed: {
      fontsLoaded () {
        return this.$store.getters.getFontsLoaded
      }
    }
  }
</script>

<style scoped>
  .footer{
    display: block;
    text-align: center;
  }
  .footer-pic{
    display: inline-block;
    vertical-align: middle;
  }
  .slide-fade-enter-active, .slide-fade-leave-active {
    transition: all .3s ease;
  }
  .slide-fade-enter, .slide-fade-leave-to {
    transform: translateY(-20px);
    opacity: 0;
  }
</style>
