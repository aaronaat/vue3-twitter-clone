<template>
  <div class="post-item" @click="favpost(post.id)">
    <div class="user-profile__post">
      <div class="post-item__user">
        @{{ username }}
      </div>
      <div class="post-item__content">
        {{ post.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostItem",
  props: {
    username: {
      type: String,
      required: true
    },
    post: {
      type: Object,
      required: true
    }
  },
  methods: {
      favpost(id) {
          this.$emit('fav', id)
      }
  }
};
</script>

<style>
.post-item {
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #DFE3E8;
  box-sizing: border-box;
  cursor: pointer;
  transition: all 0.25s ease;
  text-align:left;
}
.post-item:hover {
    transform: scale(1.05, 1.05);
  }
  .post-item__user {
    font-weight: bold;
  }

</style>