<script setup>
  import MagicalSphere from './components/MagicalSphere.vue';
  import MagicalInput from './components/MagicalInput.vue';
  import MagicalButton from './components/MagicalButton.vue';
</script>

<template>
  <header class="pt-20 pb-10">
    <h1 class="text-center text-4xl font-capsule tracking-widest">
      Magical Sphere
    </h1>
  </header>

  <main class="mt-10 mb-20 px-8 flex flex-col items-center justify-center gap-8">
    <MagicalSphere class="cursor-grab shadow-2xl shadow-black" :content="content" :is-magical="true"/>
    <p class="max-w-md text-xl text-center">
      Chose a starting value and an ending one, then click on "Pick a number" and watch the magic.
    </p>
    <div class="flex flex-wrap gap-8">
      <div class="bg-gray-900 ">
        <MagicalInput type="number" placeholder="Starts from" v-model="starts" />
      </div>
      <div class="bg-gray-900 ">
        <MagicalInput type="number" placeholder="Ends with" v-model="ends" />
      </div>
    </div>
    <div class="">
      <MagicalButton @click="pick">
        Pick a number
      </MagicalButton>
    </div>
  </main>

  <footer class="my-10 px-4 font-capsule tracking-widest">
    <div class="container mx-auto">
      <hr class="opacity-25 mb-8">
      <p class="text-center text-2xl">
        Copyright © 2025 All Rights Reserved -
        <a href="https://github.com/Mahmoud217TR" target="__blank"
          class="hover:text-rose-500 hover:text-shadow-[0_0_10px] hover:text-shadow-current transition-colors duration-300">
          MahmoudTR
        </a>
      </p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      starts: null,
      ends: null,
      content: "Wondering",
    }
  },
  methods: {
    pick() {
      if ((this.start !== null) && (this.ends !== null)) {
        let starts = parseFloat(this.starts);
        let ends = parseFloat(this.ends);

        if (ends > starts) {
          this.content = "Picked: " + this.randomNumber(starts, ends);
        } else {
          this.content = "Invalid: " + starts + " -> " + ends;
        }
      } else {
        this.content = "Wrong!";
      }
    },
    randomNumber(min, max) {
      return Math.ceil(Math.random() * (max - min) + min);
    }
  }
}
</script>
