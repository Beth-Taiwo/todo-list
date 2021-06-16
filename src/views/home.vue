<template>
  <div class="home">
    <transition name="toast">
      <toast v-if="showToast" />
    </transition>
    <todos @badValue="triggerToast" />
  </div>
</template>

<script>
import { ref } from "vue";
import toast from "../components/toast.vue";
import Todos from "../components/todos.vue";
export default {
  components: { toast, Todos },
  setup() {
    const showToast = ref(false);

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => (showToast.value = false), 3000);
    };

    return { triggerToast, showToast };
  },
};
</script>

<style>
/* .toast-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}
.toast-enter-to {
  opacity: 1;
  transform: translateY(0);
} */
.toast-enter-active {
  /* transition: all 2s ease; */
  animation: wobble 3s ease;
}
.toast-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}
.toast-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.toast-leave-active {
  transition: all 2s ease;
}
@keyframes wobble {
  0% {
    opacity: 0;
    transform: translateY(-60px);
  }
  50% {
    opacity: 1;
    transform: translateY(0);
  }
  60% {
    transform: translateX(8px);
  }
  70% {
    transform: translateX(-8px);
  }
  80% {
    transform: translateX(4px);
  }
  90% {
    transform: translateX(-4px);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
