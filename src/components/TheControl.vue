<template>
    <div class="control">
        <div class="arrow_left" @click="$emit('click-left')"></div>
        <div class="arrow_right" @click="$emit('click-right')"></div>
    </div>
</template>

<script>
export default {
  emits: ['click-left', 'click-right']
}
</script>
