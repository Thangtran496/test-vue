<template>
  <div>
    <ul v-if="posts && posts.length">
      <li v-for="post of posts" :key="post.name">
        <p>
          <strong>{{ post.id }}</strong>
        </p>
        <p>{{ post.name }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      posts: [],
      errors: [],
    };
  },

  // lấy dữ liệu khi component được tạo thành công
  created() {
    axios
      .get(`/home/products/list`)
      .then((response) => {
        this.posts = response.data;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
