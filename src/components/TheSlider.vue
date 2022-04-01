<template>
    <div class="inner">
        <div class="slider" :style="{transform: position}">
            <div class="step_slider" v-for="user in users" :key="user.id">
                <TheAvatar :stl="checked === user.id ? 'active' : ''" :idn="user.id" @chose="$emit('choseUser', $event)"/>
                <AppPersonInfo :stl="checked === user.id ? 'step_name active' : 'step_name'" :information="user.name" />
                <AppPersonInfo :stl="checked === user.id ? 'step_company active' : 'step_company'" :information="user.company.name" />
            </div>
        </div>
    </div>
</template>

<script>
import TheAvatar from './parts/TheAvatar.vue'
import AppPersonInfo from './parts/AppPersonInfo.vue'
export default {
  props: {
    users: {
      type: Array,
      required: true
    },
    checked: {
      type: Number,
      default: 0
    },
    position: {
      type: String,
      required: true,
      default: 'translateX(0px)'
    }
  },
  components: {
    TheAvatar, AppPersonInfo
  }
}
</script>
