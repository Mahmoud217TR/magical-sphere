<template>
  <div class="wrapper">
    <input v-bind="$attrs" class="input input-alt"
      :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
    <span class="input-border input-border-alt"></span>
  </div>
</template>

<script>
export default {
  name: "MagicalInput",
  props: [
    'modelValue',
  ],
  emits: ["update:modelValue"]
}
</script>

<style scoped>
.input {
  color: #fff;
  font-size: 0.9rem;
  border-radius: 0.5em;
  background-color: transparent;
  width: 100%;
  box-sizing: border-box;
  padding-inline: 0.5em;
  padding-block: 0.7em;
  border: none;
  border-bottom: var(--border-height) solid var(--border-before-color);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.input-border {
  position: absolute;
  border-radius: 0.5em;
  background: var(--border-after-color);
  width: 0%;
  height: 2px;
  bottom: 0;
  left: 0;
  transition: width 0.3s cubic-bezier(0.6, -0.28, 0.735, 0.045);
}

.input:focus {
  outline: none;
}

.input:focus + .input-border {
  width: 100%;
}

.wrapper {
  position: relative;
  border-radius: 0.5em;
  --width-of-input: 150px;
}

.input-alt {
  font-size: 1.2rem;
  padding-inline: 1em;
  padding-block: 0.8em;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.input-border-alt {
  height: 3px;
  background: linear-gradient(90deg, var(--color-blue-700) 0%, var(--color-sky-400) 50%, var(--color-white) 100%);
  transition: width 0.4s cubic-bezier(0.42, 0, 0.58, 1.00);
}

.input-alt:focus + .input-border-alt {
  width: 100%;
}
</style>
