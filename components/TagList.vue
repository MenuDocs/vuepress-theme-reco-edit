<template>
  <div class="tags">
    <span
      v-for="(item, index) in tags"
      :key="index"
      :class="{'active': item.name == currentTag}"
      @click="tagClick(item)">{{item.name}}</span>
  </div>
</template>

<script>

export default {
  props: {
    currentTag: {
      type: String,
      default: ''
    }
  },
  computed: {
    tags () {
      return [{ name: 'All Tags', path: '/tag/' }, ...this.$tags.list]
    }
  },
  methods: {
    tagClick (tag) {
      this.$emit('getCurrentTag', tag)
    }
  }
}
</script>

<style lang="stylus" scoped>
@require '../styles/mode.styl'

.tags
  margin 30px 0
  span
    vertical-align: middle;
    margin: 4px 6px 10px;
    padding: 4px 8px;
    display: inline-block;
    cursor: pointer;
    border-radius: $borderRadius
    color: #fff;
    line-height 13px
    font-size: 13px;
    box-shadow var(--box-shadow)
    transition: all .5s
    &:hover
      transform scale(1.05)
    &.active
      transform scale(1.1)
</style>
