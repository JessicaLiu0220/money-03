<template>
  <layout class-prefix="layout">
    <NumberPad />
    <Notes />
    <Types />
    <Tags :data-source.sync="tags" />
  </layout>
</template>

<script>
import NumberPad from "@/components/NumberPad.vue";
import Types from "@/components/Types.vue";
import Notes from "@/components/Notes.vue";
import Tags from "@/components/Tags.vue";
export default {
  components: { NumberPad, Types, Notes, Tags },
  data() {
    return {
      tags: ["衣", "食", "住", "行"],
    };
  },
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