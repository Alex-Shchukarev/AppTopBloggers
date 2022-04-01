<template>
    <div class="step_avatar" :class="stl" @click="$emit('chose', idn)">
        <img :src="'https://i.pravatar.cc/20'+idn">
    </div>
</template>

<script>
export default {
  emits: ['chose'],
  props: {
    idn: {
      type: Number,
      required: true
    },
    stl: {
      type: String,
      default: ''
    }
  }
}
</script>
