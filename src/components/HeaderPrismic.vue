<template>
  <header class="site-header">
    <nav>
      <ul>
        <li v-for="menuLink in menuLinks" :key="menuLink.id">
          <prismic-link :field="menuLink.link">{{ $prismic.richTextAsPlain(menuLink.label) }}</prismic-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderPrismic',
  data () {
    return {
      menuContent: [],
      menuLinks: []
    }
  },
  methods: {
    getMenu () {
      //Query to get menu content
      this.$prismic.client.getSingle('menu')
        .then((menuContent) => {
          this.menuContent = menuContent
          this.menuLinks = menuContent.data.menu_links
        })
    },
  },
  created () {
    this.getMenu()
  }
}
</script>

<style>
/* Site header */
.site-header {
  height: 30px;
  padding: 20px 0;
  margin: 0 auto;
}
.site-header,
.site-header a {
  color: #484d52;
  font-weight: 700;
}
.site-header nav a:hover {
  color: #72767B;
}
.homepage .site-header,
.homepage .site-header a {
  color: #ffffff;
}
.homepage .site-header nav a:hover {
  color: #c8c9cb;
}
.site-header .logo {
  display: inline-block;
  font-size: 22px;
  font-weight: 900;
}
.site-header nav {
  margin: auto;
  width: 70%;
}
.site-header nav ul {
  margin: 0;
}
.site-header nav li {
  display: inline-block;
  margin-left: 40px;
}
</style>

