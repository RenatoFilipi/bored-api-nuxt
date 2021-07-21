<template>
  <div>
    <div id="content">
      <div id="request">
        <h1>Are you bored?</h1>
        <button type="button" v-on:click="RequestActivity">
          Suggest Activity
        </button>
      </div>
      <div id="result">
        <p style="font-size: 1.3rem">{{ activity }}</p>
        <p>{{ participants }}</p>
      </div>
    </div>
    <Footer text="Made with Nuxt + Typescript" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Footer from "../components/Footer.vue";

interface IProps {
  activity: string;
  type: string;
  participants: string;
  price: number;
  link: string;
  key: string;
  accessibility: number;
}

export default Vue.extend({
  name: "App",
  components: {
    Footer,
  },
  data() {
    return {
      activity: "Activity will appear here :)",
      participants: "",
    };
  },
  methods: {
    async RequestActivity() {
      const response = await fetch("https://www.boredapi.com/api/activity");
      const result = (await response.json()) as Promise<IProps>;
      this.activity = (await result).activity;
      this.participants = "Participants: " + (await result).participants;
    },
  },
});
</script>

<style>
#content {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 93vh;
  gap: 2.5rem;
  color: #32475b;
}

#request {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 7rem;
}

#request h1 {
  font-size: 2.5rem;
}

#request button {
  width: 10rem;
  height: 2.5rem;
  border: none;
  background-color: #32475b;
  font: 500 1rem Poppins;
  border-radius: 3px;
  cursor: pointer;
  transition: 0.2s;
  color: #fff;
}

#request button:hover {
  background-color: #283848;
}

#result {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #32475b;
}

#result p {
  font-size: 1.2rem;
  margin: 0.5rem;
  font-size: 1rem;
}
</style>
