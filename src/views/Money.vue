<template>
  <layout class-prefix="layout">
    {{ recordList }}
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

type Record = {
  tags: string[];
  notes: string;
  type: string;
  amount: number;
  createdAt?: Date;
};
@Component({
  components: { NumberPad, Types, Notes, Tags },
})
export default class Money extends Vue {
  tags = ["衣", "食", "住", "行"];
  record: Record = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0,
  };
  recordList: Record[] = JSON.parse(
    window.localStorage.getItem("recordList") || "[]"
  );
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
    const deepClone: Record = JSON.parse(JSON.stringify(this.record));
    deepClone.createdAt = new Date();
    this.recordList.push(deepClone);
    console.log(this.recordList);
  }
  @Watch("recordList")
  onRecordListChange() {
    window.localStorage.setItem("recordList", JSON.stringify(this.recordList));
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