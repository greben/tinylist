<template>
  <div>
    <q-card-section class="content" :style="contentStyle">
      <q-icon v-if="this.$q.platform.is.mobile && draggable" class="handle text-grey-5" name="drag_indicator" size="xs" dense />
      <q-icon v-if="value.share" name="group" class="text-grey-5 shared-icon" size="xs"><q-tooltip>Shared {{ value.type }}</q-tooltip></q-icon>
      <p class="q-pa-sm text-h6 note-title">{{ value.value.title }}</p>
      <pre>{{ value.value.data }}</pre>
      <div class="clipped" v-if="clipped">&mldr;</div>
    </q-card-section>
    <q-card-actions v-if="this.$q.platform.is.desktop" class="active-buttons">
      <slot name="bottom-toolbar-left"></slot>
      <q-btn flat disabled class="invisible" />
      <q-space />
      <slot name="bottom-toolbar-right"></slot>
    </q-card-actions>
  </div>
</template>
<script>
export default {
  name: 'ViewNote',
  props: ['value', 'active', 'contentStyle', 'clipped', 'draggable']
}
</script>
<style lang="sass" scoped>
  .content
    padding: 0
    position: relative
    .note-title
      margin: 0
    pre
      margin: 0
      padding: 0 8px
      font-family: "Roboto"
      overflow-x: auto;
      white-space: pre-wrap;
      white-space: -moz-pre-wrap;
      white-space: -pre-wrap;
      white-space: -o-pre-wrap;
      word-wrap: break-word;
    .clipped
      position: absolute
      width: 100%
      bottom: 0
      height: 2.1em
      padding-top: 1em
      font-weight: 900
      font-size: 1.5em
      padding-left: 3px
      color: $grey
      background: linear-gradient(rgba(255,255,255,0), 20%, rgba(255,255,255,1))
    .shared-icon
      position: absolute
      top: -3px
      left: -1px
    .handle
      position: absolute
      top: -3px
      right: -5px
  .active-buttons
    padding: 0
</style>
