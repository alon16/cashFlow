<template>
  <layout-page>
    <template #header>
      <header-page></header-page>
    </template>
  </layout-page>
</template>
<script>
import LayoutPage from "./LayoutPage.vue";
import HeaderPage from "./HeaderPage.vue";
export default {
  components: {
    LayoutPage,
    HeaderPage,
  },
};
</script>
