<template>
  <header>
    <img @click="reload" src="@/assets/cashflow-icon.svg" alt="Logo" />
    <h1><span>Cash</span>Flow</h1>
  </header>
</template>
<script>
export default {
  methods: {
    reload() {
      location.reload();
    },
  },
};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100vw;
}
img,
span {
  width: 48px;
}
h1::after {
  content: "";
  width: 48px;
  display: inline-block;
}
h1 {
  font-size: 1.4rem;
  color: var(--brand-blue);
}
h1 span {
  color: var(--brand-green);
}
</style>
