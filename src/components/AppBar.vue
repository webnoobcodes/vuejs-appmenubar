<template>
  <div class="container">
    <div class="nav-icon">
      <i class="fas fa-bars fa-fw" v-if="!showNav" @click="showNavbar"></i>
      <i class="fas fa-times fa-fw" v-else @click="hideNavbar"></i>
    </div>
    <transition name="fade">
      <div class="nav-container" v-if="showNav">
        <transition-group class="app-wrapper" name="slide-in">
          <div class="app-container" 
            v-for="(app, i) in getApps" 
            :key="'app'+i"
            :style="{'--i':i}">
            <div class="app-card"
              :style="{'background':'linear-gradient(to bottom, '+app.colorTop+', '+app.colorBottom+')'}">
              <i :class="app.icon"></i>
            </div>
            <div class="app-title">
              {{ app.title }}
            </div>
          </div>          
        </transition-group>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    data: () => {
      return {
        showNav: false,
        showApps: false,
        apps: [
          { title: 'Home', icon: 'fas fa-igloo fa-fw', colorTop: '#D1FE77', colorBottom: '#84B241' },
          { title: 'Message', icon: 'fas fa-comment-dots fa-fw', colorTop: '#FEFB81', colorBottom: '#E5AD4C' },
          { title: 'Contact', icon: 'fas fa-envelope fa-fw', colorTop: '#DEB59A', colorBottom: '#A78772' },
          { title: 'Search', icon: 'fas fa-search fa-fw', colorTop: '#B5BEFF', colorBottom: '#99A0E4' },
          { title: 'Downloads', icon: 'fas fa-cloud-download-alt fa-fw', colorTop: '#FD5D64', colorBottom: '#FF494E' },
          { title: 'Gallery', icon: 'fas fa-image fa-fw', colorTop: '#A7A8AB', colorBottom: '#8C8E91' },
          { title: 'About', icon: 'fas fa-user fa-fw', colorTop: '#83E9FE', colorBottom: '#71C7FA' },
          { title: 'Calendar', icon: 'fas fa-calendar-alt fa-fw', colorTop: '#84F9B2', colorBottom: '#6CCC91' },
          { title: 'Youtube', icon: 'fab fa-youtube fa-fw', colorTop: '#FD5D64', colorBottom: '#FF494E' },
          { title: 'Twitter', icon: 'fab fa-twitter fa-fw', colorTop: '#83E9FE', colorBottom: '#71C7FA' },
          { title: 'Instagram', icon: 'fab fa-instagram fa-fw', colorTop: '#B5BEFF', colorBottom: '#99A0E4' },
          { title: 'Pinterest', icon: 'fab fa-pinterest fa-fw', colorTop: '#FD5D64', colorBottom: '#FF494E' },
        ]
      }
    },
    computed: {
      getApps() {
        return this.showApps === true ? this.apps : [];
      }
    },
    methods: {
      showNavbar() {
        this.showNav = !this.showNav;
        setTimeout(() => {
          this.showApps = true;  
        }, 600);
      },
      hideNavbar() {
        this.showNav = !this.showNav;
        this.showApps = !this.showApps;
      }
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    background: url('../assets/app_bg_z.jpg') center center;
    background-attachment: fixed;
    background-size: cover;
    width: 100%;
    min-height: 100vh;
    overflow: hidden;
  }

  .nav-icon {
    position: absolute;
    top: 0;
    right: 0;
    padding: 20px;
    z-index: 999;

    i {
      color: #fff;
      font-size: 2rem;
      cursor: pointer;
    }
  }

  .nav-container {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-height: 100vh;
    background: inherit;
    overflow: hidden;

    &:before {
      content: '';
      position: absolute;
      width: 100%;
      min-height: 100vh;
      background: inherit;
      box-shadow: inset 0 0 0 1000px rgba(0,0,0,.5);
      filter: blur(10px);
      z-index: 10;
    }

    .app-wrapper {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      width: 100%;
      max-width: 720px;
    }
  }

  .app-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 20px;
    z-index: 11;

    .app-card {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 80px;
      height: 80px;
      border-radius: 20px;
      box-shadow: 5px 5px 10px 0 rgba(0,0,0,.4);
      font-size: 3rem;
      cursor: pointer;
      transition: transform .2s ease-in-out;

      i {
        color: #fff;
      }

      &:hover {
        transform: scale(1.1);
      }
    }

    .app-title {
      color: #fff;
      font-size: 1.2rem;
      padding-top: 10px;
    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: all .8s ease-in-out;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

  .slide-in-enter-active, .slide-in-leave-active {
    transition: opacity .5s linear, transform .5s cubic-bezier(.2, .5, .1, 1);
    transition-delay: calc(.1s * var(--i));
  }
  .slide-in-enter, .slide-in-leave-to {
    opacity: 0;
    transform: translateX(-1em);
  }
</style>
