<template>
    <div
      @dragstart.self="onDrag"
      draggable
      @dragover.prevent
      @dragenter.prevent
    >
      <slot />
    </div>
</template>

<script>
export default {
  props: {
    transferData: {
      type: Object,
      required: true
    }
  },
  methods: {
    onDrag (e) {
      e.dataTransfer.effectAlowed = 'move'
      e.dataTransfer.dropEffect = 'move'
      e.dataTransfer.setData('payload', JSON.stringify(this.transferData))
    }
  }
}
</script>

<style scoped>

</style>