<template>
  <div class="container">
    <TheHeader />
    <TheControl @click-left="downLeft" @click-right="downRight"/>
    <div v-if="!isLoadUsersSuccess"><AppLoader /></div>
    <div v-else>
      <TheSlider :users="users" :checked="activeUserId" :position="styleParam" @chose-user="choseUserId"/>
    </div>
    <div v-if="isLoadPostsSuccess"><ThePostsUser :posts="getPostsUser" :user="getUserName"/></div>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import TheControl from './components/TheControl.vue'
import AppLoader from './components/AppLoader.vue'
import TheSlider from './components/TheSlider.vue'
import ThePostsUser from './components/ThePostsUser.vue'
import axios from 'axios'
export default {
  data () {
    return {
      users: [],
      posts: [],
      threePosts: [],
      activeUserId: 0,
      isLoadUsersSuccess: false,
      isLoadPostsSuccess: false,
      step: 324,
      currentPosition: 1,
      styleParam: ''
    }
  },
  mounted () {
    this.getUsers()
  },
  methods: {
    async getUsers () {
      const { data } = await axios.get('https://jsonplaceholder.typicode.com/users')
      this.users = [...data]
      this.isLoadUsersSuccess = true
    },
    async getPosts () {
      const { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts?userId=${this.activeUserId}`)
      this.posts = [...data]
      this.isLoadPostsSuccess = true
    },
    downRight () {
      if (this.currentPosition < 7) {
        this.styleParam = `translateX(-${this.step * this.currentPosition}px)`
        this.currentPosition += 1
      }
    },
    downLeft () {
      if (this.currentPosition > 1) {
        this.styleParam = `translateX(-${this.step * (this.currentPosition - 2)}px)`
        this.currentPosition -= 1
      }
    },
    choseUserId (userId) {
      this.activeUserId = userId
      this.getPosts()
    }
  },
  computed: {
    getUserName () {
      return this.users[this.activeUserId - 1].name
    },
    getPostsUser () {
      return this.posts.filter((p, i) => i > 1 && i < 5)
    }
  },
  components: {
    TheHeader, TheControl, AppLoader, TheSlider, ThePostsUser
  }
}
</script>

<style>
</style>
