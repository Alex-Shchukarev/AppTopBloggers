<template>
    <div class="posts">
        <div class="posts_header">3 актуальных поста {{ user }}</div>
        <div class="posts_inner">
            <div class="post" v-for="post in posts" :key="post.id">
                <AppPersonInfo stl="post_header" :information="post.title" />
                <AppPersonInfo stl="post_text" :information="post.body" />
            </div>
        </div>
    </div>
</template>

<script>
import AppPersonInfo from './parts/AppPersonInfo.vue'
export default {
  props: {
    posts: {
      type: Array,
      required: true
    },
    user: {
      type: String
    }
  },
  components: {
    AppPersonInfo
  }
}
</script>
