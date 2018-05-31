<template>
  <div class="feed">
    <template v-if="loading > 0">
        Loading...
</template>

<template v-else>
  <ul>
    <li v-for="name in allNames" :key="name.id">
      <name :name='name' class="name" />
    </li>
  </ul>
</template>
  </div>
</template>

<style>
  /*.name {
    margin-bottom: 20px;
    background-color:gray;
    border-radius:20px;
    border-shadow
  }*/
  
  .name {
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    width: 300px;
    height: 300px;
    float: left;
  }
  
  ul {
    list-style: none outside none;
  }
  
  li {
    position: relative;
    display: inline;
  }
  
  
  /* On mouse-over, add a deeper shadow */
  
  .name:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
</style>

<script>
  import gql from 'graphql-tag'
  import Name from './Name.vue'
  
  // GraphQL query
  const FeedQuery = gql `
    query allNames {
      allNames(orderBy: createdAt_DESC) {
        id
        name
      }
    }
  `
  
  // Component def
  export default {
    // Local state
    data: () => ({
      allNames: {},
      loading: 0,
    }),
    // Apollo GraphQL
    apollo: {
      allNames: {
        query: FeedQuery,
        loadingKey: 'loading',
      },
    },
    components: {
      // <my-component> will only be available in parent's template
      'name': Name
    }
  }
</script>
