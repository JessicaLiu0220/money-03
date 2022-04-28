<template>
  <layout class-prefix="layout">
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord" />
    <Notes @update:value="onUpdateNotes" />
    <Types @update:value="onUpdateType" />
    <Tags :data-source.sync="tags" @update:value="onUpdateTags" />
  </layout>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Watch } from "vue-property-decorator";
import NumberPad from "@/components/NumberPad.vue";
import Types from "@/components/Types.vue";
import Notes from "@/components/Notes.vue";
import Tags from "@/components/Tags.vue";
import model from "@/model";

@Component({
  components: { NumberPad, Types, Notes, Tags },
})
export default class Money extends Vue {
  tags = ["衣", "食", "住", "行"];
  record: RecordItem = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0,
  };
  recordList = model.fetch();
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
  saveRecord() {
    const deepClone: RecordItem = model.clone(this.record);
    deepClone.createdAt = new Date();
    this.recordList.push(deepClone);
    console.log(this.recordList);
  }
  @Watch("recordList")
  onRecordListChange() {
    model.save(this.recordList);
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