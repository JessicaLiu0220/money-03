<template>
  <layout class-prefix="layout">
    {{ record }}
    <NumberPad @update:value="onUpdateAmount" />
    <Notes @update:value="onUpdateNotes" />
    <Types @update:value="onUpdateType" />
    <Tags :data-source.sync="tags" @update:value="onUpdateTags" />
  </layout>
</template>

<script lang="ts">
import Vue from "vue";
import { Component } from "vue-property-decorator";
import NumberPad from "@/components/NumberPad.vue";
import Types from "@/components/Types.vue";
import Notes from "@/components/Notes.vue";
import Tags from "@/components/Tags.vue";

type Record = {
  tags: string[];
  notes: string;
  type: string;
  amount: number;
};
@Component({
  components: { NumberPad, Types, Notes, Tags },
})
export default class Money extends Vue {
  tags = ["衣", "食", "住", "行"];
  record: Record = {
    tags: [],
    notes: "",
    type: "",
    amount: 0,
  };
  onUpdateTags(tag: string[]) {
    this.record.tags = tag;
  }
  onUpdateNotes(notes: string) {
    this.record.notes = notes;
  }
  onUpdateType(type: string) {
    this.record.type = type;
  }
  onUpdateAmount(value: string) {
    this.record.amount = parseFloat(value);
  }
}
</script>

<style lang="scss">
.layout-concern {
  display: flex;
  flex-direction: column-reverse;
}
</style>

<style lang="scss" scoped>
</style>