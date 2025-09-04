<template>
  <div class="container">
  <button class="button" v-bind="$attrs">
    <slot></slot>
  </button>
</div>

</template>

<script>
export default {
  name: "MagicalButton",
}
</script>

<style scoped>
button {
  font-size: 1.4em;
  padding: 0.6em 0.8em;
  border-radius: 0.5em;
  border: none;
  background-color: var(--color-black);
  color: var(--color-white);
  cursor: pointer;
  box-shadow: 2px 2px 3px #000000b4;
}

.container {
  position: relative;
  padding: 3px;
  background: linear-gradient(90deg, var(--color-indigo-400), var(--color-purple-600));
  border-radius: 0.9em;
  transition: all 0.4s ease;
}

.container::before {
  content: "";
  position: absolute;
  inset: 0;
  margin: auto;
  border-radius: 0.9em;
  z-index: -10;
  filter: blur(0);
  transition: filter 0.4s ease;
}

.container:hover::before {
  background: linear-gradient(90deg, var(--color-indigo-400), var(--color-purple-600));
  filter: blur(1.2em);
}
.container:active::before {
  filter: blur(0.2em);
}
</style>
