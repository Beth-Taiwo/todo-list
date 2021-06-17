<template>
  <div class="about">
    <transition
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
    >
      <h1>About</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis error
      temporibus similique incidunt, perspiciatis et cumque a commodi placeat
      vitae, quidem officia expedita neque reiciendis animi accusantium fugiat
      nam odio.
    </p>
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptatem iusto
      odit autem facilis voluptate eum iste consequuntur earum cumque aut?
      Quibusdam voluptatibus porro quidem cupiditate. Fugiat iusto voluptatibus
      hic placeat.
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Fuga non quos
      cupiditate quis accusantium voluptates eum soluta blanditiis minima eaque.
      Natus veniam velit asperiores consequatur maxime quisquam laboriosam,
      delectus numquam!
    </p>
  </div>
</template>

<script>
// import { ref } from "vue";
import gsap from "gsap";
export default {
  setup() {
    const beforeEnter = (el) => {
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
      console.log("before enter");
    };

    const enter = (el, done) => {
      gsap.to(el, {
        duration: 3,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
        onComplete: done,
      });
      console.log("enter");
    };
    const afterEnter = (el) => {
      console.log("after Enter", el);
      // el.style.color = "red";
      // setTimeout(() => (showTitle.value = false), 2000);
      // el.style.value
    };
    const beforeLeave = () => {
      console.log("before leave");
    };
    const leave = () => {
      console.log("leave");
    };
    const afterLeave = () => {
      console.log("after leave");
      // setTimeout(() => (showTitle.value = true), 1000);
    };

    return {
      beforeEnter,
      // showTitle,
      afterEnter,
      enter,
      beforeLeave,
      leave,
      afterLeave,
    };
  },
};
</script>

<style>
.about {
  max-width: 600px;
  margin: 20px auto;
}
</style>
