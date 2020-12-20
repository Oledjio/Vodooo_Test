<template>
  <div class="users">
    <input
      type="text"
      class="users__search"
      placeholder="Введите имя автора"
      @input="usersSearch"
      v-model="searchQuery"
    />
    <ul class="list">
      <ListItem
        :post="combineUserAndPost"
        :key="combineUserAndPost"
        v-for="combineUserAndPost of posts"
      />
    </ul>
  </div>
</template>

<script>
import ListItem from "@/components/ListItem";
export default {
  data() {
    return {
      posts: this.combineUserAndPost,
      searchQuery: ""
    };
  },
  props: ["combineUserAndPost"],
  components: {
    ListItem
  },
  methods: {
    usersSearch() {
      this.posts = this.combineUserAndPost.filter(post =>
        post.name.includes(this.searchQuery)
      );
    }
  }
};
</script>

<style lang="sass">
.list
    display: flex
    flex-wrap: wrap
    @include tablet
        justify-content: space-between
.users
    background-color: #d5d5e0
    display: flex
    flex-direction: column
    align-items: center
    padding-top: 20px
    padding: 30px 50px
    @include tablet
        padding: 50px 15px
.users__search
    border: 1px solid grey
    border-radius: 3px
    padding: 10px 40px
    padding-left: 15px
    margin-bottom: 20px
    @include tablet
        width: 100%
    &:focus
        outline: none
</style>
