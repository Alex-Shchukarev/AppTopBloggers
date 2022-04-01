<template>
    <div :class="stl"> {{ information }} </div>
</template>

<script>
export default {
  props: {
    information: {
      type: String,
      required: true,
      default: 'Unknown'
    },
    stl: {
      type: String,
      required: true,
      default: 'card'
    }
  }
}
</script>
