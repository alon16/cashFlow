<template>
  <layout-page>
    <template #header>
      <header-page></header-page>
    </template>
    <template #resume>
      <resume-page></resume-page>
    </template>
    <template #movements>
      <movements-page></movements-page>
    </template>
  </layout-page>
</template>
<script>
import LayoutPage from "./LayoutPage.vue";
import HeaderPage from "./HeaderPage.vue";
import ResumePage from "./Resume/IndexPage.vue";
import MovementsPage from "./MovementsPage.vue";
export default {
  components: {
    LayoutPage,
    HeaderPage,
    ResumePage,
    MovementsPage,
  },
};
</script>
