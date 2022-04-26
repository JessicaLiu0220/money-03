<template>
  <layout class-prefix="layout">
    <NumberPad />
    <Notes />
    <Types />
    <Tags />
  </layout>
</template>

<script>
import NumberPad from "@/components/NumberPad.vue";
import Types from "@/components/Types.vue";
import Notes from "@/components/Notes.vue";
import Tags from "@/components/Tags.vue";
export default {
  components: { NumberPad, Types, Notes, Tags },
};
</script>

<style lang="scss">
.layout-concern {
  display: flex;
  flex-direction: column-reverse;
}
</style>

<style lang="scss" scoped>
</style>