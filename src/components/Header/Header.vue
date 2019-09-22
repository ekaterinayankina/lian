<template>
  <div class="header">
    <div class="logo">
      <img class="logo__img" src="../../assets/logo.png" alt="LIAN"/>
    </div>
    <div class="menu-wrapper">
      <ul id="menu">
        <li v-for="item in menu_items" v-bind:key="item.id">
          {{ item.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data: () => {
    return {
      menu_items: [
        { title: 'Home', link: '#' },
        { title: 'About', link: '#' },
        { title: 'Portfolio', link: '#' },
        { title: 'Blog', link: '#' },
        { title: 'Contact', link: '#' }
      ]
    }
  }
}
</script>

<style lang="scss">
  @import "../../assets/scss/common.scss";
  .header {
    margin: 0 auto;
    width: 80%;
    min-height: 37px;
    padding: 0 15px;
    overflow: auto;
  }

  .logo {
    display: inline-block;
    float: left;
    padding-top: 6px;
      &__img {
        width: 66px;
        height: 17px;
      }
  }
  .menu-wrapper {
    float: right;
    width: 44%;
    max-width: 270px;
    padding-right: 5px;
  }
  #menu {
    display: flex;
    justify-content: space-between;
    margin: 11px 0;
    padding: 0;
    li {
      display: inline-block;
      text-transform: uppercase;
      font-size: 0.45em;
      font-weight: 600;
      letter-spacing: .5px;
      color: $link-color;
      &:hover {
        color: black;
        cursor: pointer;
      }
    }
  }
</style>
