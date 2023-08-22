<script>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

const DARK_THEME_ID = 'dark-theme'
const LIGHT_THEME_ID = 'light-theme'
const DARK_GRAY_THEME_PATH = '/src/assets/theme-dark-gray.css'
const LIGHT_GREEN_THEME_PATH = '/src/assets/theme-light-green.css'

export default {
  components: { HelloWorld, TheWelcome },
  setup() {
    function addLinkElt(id, styleSheetPath, disabled) {
      const newLinkElt = document.createElement('link');
      newLinkElt.id = id;
      newLinkElt.rel = 'stylesheet';
      newLinkElt.media = disabled ? 'none' : '';
      newLinkElt.href = styleSheetPath
      const titleElt = document.getElementsByTagName('title')[0]
      document.head.insertBefore(newLinkElt, titleElt)
    }

    addLinkElt(DARK_THEME_ID, DARK_GRAY_THEME_PATH, false)
    addLinkElt(LIGHT_THEME_ID, LIGHT_GREEN_THEME_PATH, true)
  }
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
