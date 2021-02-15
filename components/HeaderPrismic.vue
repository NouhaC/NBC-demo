<template>
  <header class="site-header">
    <p v-if="$store.state.menu === 'Please create a menu document'" class="logo">{{ $store.state.menu }}</p>
    <div class="logo-icon">
      <nuxt-link to="/" class="logo"><img src="https://marinersmuseum.org/wp-content/uploads/2018/06/nothing-bundt-cakes-logo.png"></nuxt-link>
    </div>
    <nav class="menu">
      <ul>
        <li v-for="menuLink in $store.state.menu.menu_links" :key="menuLink.id">
          <prismic-link :field="menuLink.link">{{ $prismic.asText(menuLink.label) }}</prismic-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'header-prismic',
}
</script>

<style lang="sass">
.site-header
  position: relative
  overflow: auto
  padding: 20px 0
  color: #484d52
  font-weight: 700
  a
    color: #484d52
    font-weight: 700


.homepage .site-header
  color: #ffffff
  a
    color: #ffffff
  nav a:hover
    color: #c8c9cb

.site-header
  .logo-icon
    width: 20%; 
    height: 20%; 
    object-fit: contain; 
.menu
  a:hover
    color: #72767B
  float: right
  ul
    margin: 0
    padding-left: 0
  li
    display: inline-block
    margin-left: 40px

@media (max-width: 1060px)
  .site-header
    padding-left: 20px
    padding-right: 20px

@media (max-width: 767px)
  .site-header
    height: auto

  .homepage .site-header
    position: absolute
    left: 0
    right: 0

  .site-header
    .logo
      display: block
      text-align: center
    nav
      float: none
      text-align: center
      li
        display: inline-block
        margin-left: 10px
        margin-right: 10px
</style>


