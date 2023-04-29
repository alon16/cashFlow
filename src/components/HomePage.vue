<template>
  <layout-page>
    <template #header>
      <header-page></header-page>
    </template>
    <template #resume>
      <resume-page :label="label" :amount="amount" :total-amount="1000000">
        <template #graphic> graphic </template>
        <template #action> action </template>
      </resume-page>
    </template>
    <template #movements>
      <movements-page :movements="movements"></movements-page>
    </template>
  </layout-page>
</template>
<script>
import LayoutPage from "./LayoutPage.vue";
import HeaderPage from "./HeaderPage.vue";
import ResumePage from "./Resume/IndexPage.vue";
import MovementsPage from "./Movement/IndexPage.vue";
export default {
  components: {
    LayoutPage,
    HeaderPage,
    ResumePage,
    MovementsPage,
  },
  data() {
    return {
      amount: null,
      label: "",
      movements: [
        {
          id: 0,
          title: "MOVIMIENTO Inicial",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 1,
          title: "MOVIMIENTO 1",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 2,
          title: "MOVIMIENTO 2",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 3,
          title: "MOVIMIENTO 3",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 4,
          title: "MOVIMIENTO 4",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 5,
          title: "MOVIMIENTO 5",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 6,
          title: "MOVIMIENTO 6",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 7,
          title: "MOVIMIENTO 7",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 8,
          title: "MOVIMIENTO 8",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 9,
          title: "MOVIMIENTO 9",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
        {
          id: 10,
          title: "MOVIMIENTO 10",
          description: "Lorem ipsum sit",
          amount: 1000,
        },
      ],
    };
  },
};
</script>
