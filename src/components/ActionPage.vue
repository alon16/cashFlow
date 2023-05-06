<template>
  <div>
    <button @click="showModal = true">Agregar movimiento</button>
    <teleport to="#app">
      <div v-show="showModal">Modal</div>
      <modal-page v-show="showModal" @close="showModal = false">
        <form @submit.prevent="submit">
          <div class="field">
            <label for="">Título</label>
            <input type="text" v-model="movement.title" />
          </div>
          <div class="field">
            <label for="">Monto</label>
            <input type="number" v-model="movement.amount" />
          </div>
          <div class="field">
            <label for="">Descripción</label>
            <textarea rows="4" v-model="movement.description" />
          </div>
          <div class="field">
            <label for="">Tipo de movimiento</label>
            <label class="radio-label">
              <input type="radio" v-model="movement.type" value="Ingreso" />
              <span>Ingreso</span>
            </label>
            <label class="radio-label">
              <input type="radio" v-model="movement.type" value="Gasto" />
              <span>Gasto</span>
            </label>
          </div>
          <div class="action">
            <button type>Agregar Movimiento</button>
          </div>
        </form>
      </modal-page>
    </teleport>
  </div>
</template>
<script setup>
import { ref } from "vue";
import ModalPage from "./ModalPage.vue";
const showModal = ref(false);
const movement = ref({
  title: "",
  amount: 0,
  description: "",
  type: "Ingreso",
});
const submit = () => {
  showModal.value = false;
};
</script>
<style scoped>
button {
  color: white;
  font-size: 1.25rem;
  background-color: var(--brand-blue);
  border: none;
  width: 100%;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
  cursor: pointer;
}

form {
  font-size: 1.24rem;
  width: 100%;
}

form .action {
  padding: 0 24px;
}

.field {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 16px 24px;
}

label {
  margin-bottom: 8px;
}

input,
textarea {
  font-size: 1.24rem;
  border: 2px solid var(--brand-blue);
  border-radius: 8px;
  padding: 8px;
}

input[type="number"] {
  text-align: right;
}

.radio-label {
  display: flex;
  align-items: center;
  margin-top: 8px;
}

.radio-label span {
  margin-top: 4px;
  margin-left: 8px;
}

input[type="radio"] {
  appearance: none;
  width: 1.24rem;
  height: 1.24rem;
  color: var(--brand-blue);
  border: 2px solid var(--brand-blue);
  border-radius: 50%;
}

input[type="radio"]:checked {
  background-color: var(--brand-blue);
}
</style>
