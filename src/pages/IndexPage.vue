<template>
  <q-page class="flex flex-center">
    <q-btn
      color="white"
      text-color="black"
      label="Sign In via Whatsapp"
      @click="() => sendMsg('+919404879730', 'Hey can you help me sign in?')"
    />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  methods: {
    async getPosts() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts"
      );
      const posts = await response.json();
      console.log(posts);
    },
    sendMsg(number, message) {
      console.log("number", number);
      console.log("message", message);
      var url =
        "https://api.whatsapp.com/send?phone=" +
        number +
        "&text=" +
        encodeURIComponent(message);

      (async () => {
        try {
          window.open(url, "_blank").focus();
        } catch (error) {
          console.log("error", error);
        }
      })();

      return url;
    },
  },
});
</script>
