<template>
  <div class="home">
    <modal @close="toggleModal" :modalActive="modalActive">
      <div class="modal-content">
        <h1>Charm Friend Lovers</h1>
        <p>
          Jennings vicinity subject greatly. Your folly hundred miles norland dejection misery delay blushes forbade. Length much humanity rest girl. Extensive invitation especially vulgar truth six
          match marriage compact alone females because intention cultivated prevailed. Passed over moderate joy aware resembled children paid astonished hastily wicket gentleman desirous continuing
          among kindness dine.
        </p>
      </div>
    </modal>
    <button @click="toggleModal" type="button">Open Modal</button>
  </div>
</template>

<script>
  import Modal from '../components/Modal.vue';
  import { ref } from 'vue';

  export default {
    name: 'Home',
    components: {
      Modal,
    },
    setup() {
      const modalActive = ref(false);

      const toggleModal = () => {
        modalActive.value = !modalActive.value;
      };

      return { modalActive, toggleModal };
    },
  };
</script>

<style lang="scss" scoped>
  .home {
    background: linear-gradient(145deg, #004de6, #005bff);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal-content {
    display: flex;
    flex-direction: column;
    h1,
    p {
      margin-bottom: 1rem;
    }

    h1 {
      font-size: 2rem;
    }

    p {
      font-size: 1rem;
      margin-bottom: 2rem;
    }
  }
</style>
