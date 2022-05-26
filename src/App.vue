<template>
  <NavbarItem />
  <div class="wrapper">
    <TextForm
      >Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae
      necessitatibus exercitationem cum nostrum facilis totam similique!
      Inventore eos a obcaecati, exercitationem rem fuga cumque assumenda
      excepturi dolor iste repellendus odit?</TextForm
    >
  </div>
</template>

<script>
import NavbarItem from "./components/NavbarItem.vue";
import TextForm from "./components/TextForm.vue";

export default {
  name: "App",
  components: {
    NavbarItem,
    TextForm,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  width: 1200px;
  margin: 50px auto 0 auto;
}
</style>
