<template>
  <div class="wrapper">
    <div class="container">
      <List :combineUserAndPost="combineUserAndPost" />
    </div>
  </div>
</template>

<script>
import List from "@/components/List";

export default {
  name: "App",
  data() {
    return {
      urlPost: "https://jsonplaceholder.typicode.com/posts",
      urlUsers: "https://jsonplaceholder.typicode.com/users",
      combineUserAndPost: []
    };
  },
  components: {
    List
  },
  mounted() {
    this.getUsers();
  },
  methods: {
    async getUsers() {
      let responsePost = await fetch(this.urlPost);
      let resultPost = await responsePost.json();
      let totalPost = [...resultPost.slice(0, 6)];

      let responseUsers = await fetch(this.urlUsers);
      let resultUsers = await responseUsers.json();
      let totalUsers = [...resultUsers.slice(0, 6)];

      totalPost.forEach(
        (item, index) => (item["name"] = totalUsers[index].name)
      );

      this.combineUserAndPost.push(...totalPost);
    }
  }
};
</script>
