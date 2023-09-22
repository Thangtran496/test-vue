<template>
  <div>
    <button class="btn btn-primary">hi</button>
    <table >
      <thead>
        name
      </thead>
      <td>
        <tr v-if="posts && posts.length">
          <ul v-for="post in posts" :key="post.id">
            <p>{{ post.name }}</p>
          </ul>
        </tr>
      </td>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      posts: [],
      data: [],
    };
  },

  // lấy dữ liệu khi component được tạo thành công
  mounted() {
    axios
      .get(`/rest/category`)
      .then((response) => {
        this.posts = response.data;
      })
      .catch((e) => {

      });
  },
};
</script>
