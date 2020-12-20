<template>
  <li class="list__item">
    <p class="list__header">{{ post.title }}</p>
    <p class="list__text">{{ post.body }}</p>
    <p class="list__author">{{ post.name }}</p>
  </li>
</template>

<script>
export default {
  props: ["post"]
};
</script>

<style lang="sass">

.list__text
    margin-bottom: 15px
.list__item
    margin-bottom: 15px
    background-color: white
    padding: 15px
    border-radius: 5px
    width: calc(34% - 22px)
    margin-right: 20px
    height: fit-content
    &:nth-child(3n)
        margin-right: 0
    @include tablet
        width: calc(50% - 10px)
        margin-right: 0
    @include mobile
        flex: 1 0 100%
.list__header
    margin-bottom: 20px
    color: #2d4ffa
    font-weight: bold
.list__author
    color: #9a9ab3
</style>
