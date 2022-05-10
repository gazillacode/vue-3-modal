<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal">
      <transition name="modal-animation-inner">
        <div v-show="modalActive" class="modal__inner">
          <i @click="close" class="fa-regular fa-circle-xmark"></i>
          <!-- Modal Content -->
          <slot />
          <button @click="close" type="button">Close</button>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
  export default {
    props: ['modalActive'],
    setup(props, { emit }) {
      const close = () => {
        emit('close');
      };

      return { close };
    },
  };
</script>

<style lang="scss" scoped>
  .modal-animation-enter-active,
  .modal-animation-leave-active {
    transition: opacity 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }

  .modal-animation-enter-from,
  .modal-animation-leave-to {
    opacity: 0;
  }

  .modal-animation-inner-enter-active {
    transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275) 0.15s;
  }

  .modal-animation-inner-leave-active {
    transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }

  .modal-animation-inner-enter-from {
    opacity: 0;
    transform: scale(0.8);
  }

  .modal-animation-inner-leave-to {
    transform: scale(0.8);
  }

  .modal {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw;
    position: fixed;
    inset: 0;
  }
  .modal__inner {
    position: relative;
    max-width: 600px;
    width: 90%;
    border-radius: 11px;
    background: linear-gradient(145deg, #004de6, #005bff);
    box-shadow: 26px 26px 52px #0048d9, -26px -26px 52px #0062ff;
    padding: 4rem;
    color: white;

    i {
      position: absolute;
      top: 1rem;
      right: 1rem;
      font-size: 20px;
      cursor: pointer;
      transition: 0.2s all ease;
      &:hover {
        opacity: 0.6;
      }
    }

    button {
      padding: 1rem 2rem;
      border: none;
      font-size: 1rem;
      background-color: white;
      color: #004de6;
      cursor: pointer;
    }
  }
</style>
