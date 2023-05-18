<template>
  <layout-page>
    <template #header>
      <header-page></header-page>
    </template>
    <template #resume>
      <resume-page :label="label" :amount="amount" :total-amount="totalAmount">
        <template #graphic>
          <graphic-page :amounts="amounts" @selected="select"></graphic-page>
        </template>
        <template #action>
          <action-page @created="create"></action-page
        ></template>
      </resume-page>
    </template>
    <template #movements>
      <movements-page :movements="movements" @removed="remove"></movements-page>
    </template>
  </layout-page>
</template>
<script>
import LayoutPage from "./LayoutPage.vue";
import HeaderPage from "./HeaderPage.vue";
import ResumePage from "./Resume/IndexPage.vue";
import MovementsPage from "./Movement/IndexPage.vue";
import ActionPage from "./ActionPage.vue";
import GraphicPage from "./Resume/GraphicPage.vue";
export default {
  components: {
    LayoutPage,
    HeaderPage,
    ResumePage,
    MovementsPage,
    ActionPage,
    GraphicPage,
  },
  data() {
    return {
      amount: null,
      label: "",
      movements: [],
    };
  },
  computed: {
    amounts() {
      let lastDays = this.movements
        .filter((m) => {
          let today = new Date();
          let oldDays = today.setDate(today.getDate() - 30);
          return m.time > oldDays;
        })
        .map((m) => m.amount);

      return lastDays.map((m, i) => {
        let lastMovements = lastDays.slice(0, i + 1);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
    totalAmount() {
      return this.movements.reduce((suma, m) => {
        return suma + m.amount;
      }, 0);
    },
  },
  mounted() {
    const movements = JSON.parse(localStorage.getItem("movements"));
    if (Array.isArray(movements)) {
      this.movements = movements.map((m) => {
        return { ...m, time: new Date(m.time) };
      });
    }
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
      this.save();
    },
    remove(id) {
      let index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
      this.save();
    },
    save() {
      localStorage.setItem("movements", JSON.stringify(this.movements));
    },
    select(val) {
      this.amount = val;
    },
  },
};
</script>
