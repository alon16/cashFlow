<template>
  <layout-page>
    <template #header>
      <header-page></header-page>
    </template>
    <template #resume>
      <resume-page :label="label" :amount="amount" :total-amount="1000000">
        <template #graphic>
          <graphic-page :amounts="amounts"></graphic-page>
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
      movements: [
        {
          id: 0,
          title: "MOVIMIENTO Inicial",
          description: "Lorem ipsum sit",
          amount: 100,
          time: new Date("05-01-2023"),
        },
        {
          id: 1,
          title: "MOVIMIENTO 1",
          description: "Lorem ipsum sit",
          amount: 200,
          time: new Date("05-01-2023"),
        },
        {
          id: 2,
          title: "MOVIMIENTO 2",
          description: "Lorem ipsum sit",
          amount: 500,
          time: new Date("05-01-2023"),
        },
        {
          id: 3,
          title: "MOVIMIENTO 3",
          description: "Lorem ipsum sit",
          amount: 200,
          time: new Date("05-01-2023"),
        },
        {
          id: 4,
          title: "MOVIMIENTO 4",
          description: "Lorem ipsum sit",
          amount: -400,
          time: new Date("05-01-2023"),
        },
        {
          id: 5,
          title: "MOVIMIENTO 5",
          description: "Lorem ipsum sit",
          amount: -600,
          time: new Date("05-01-2023"),
        },
        {
          id: 6,
          title: "MOVIMIENTO 6",
          description: "Lorem ipsum sit",
          amount: -300,
          time: new Date("05-01-2023"),
        },
        {
          id: 7,
          title: "MOVIMIENTO 7",
          description: "Lorem ipsum sit",
          amount: 0,
          time: new Date("05-01-2023"),
        },
        {
          id: 8,
          title: "MOVIMIENTO 8",
          description: "Lorem ipsum sit",
          amount: 300,
          time: new Date("05-01-2023"),
        },
        {
          id: 9,
          title: "MOVIMIENTO 9",
          description: "Lorem ipsum sit",
          amount: 500,
          time: new Date("05-01-2023"),
        },
        {
          id: 10,
          title: "MOVIMIENTO 10",
          description: "Lorem ipsum sit",
          amount: 0,
          time: new Date("04-01-2023"),
        },
      ],
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
        let lastMovements = lastDays.slice(0, i);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
    },
    remove(id) {
      let index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
    },
  },
};
</script>
