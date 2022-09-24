<script lang="ts">
import { defineComponent, PropType } from "vue";
import CompInfo from "./CompInfo.vue";
// fetch('https://jsonplaceholder.typicode.com/todos/1')
//     .then(response => response.json())
//     .then(json => console.log(json))
export default defineComponent({
  name: "CompListInfo",
  components: {
    CompInfo,
  },
  props: {
    listInfo: {
      type: Array as any,
      default: () => [],
    },
  },
  data() {
    return {
      filterSelect: "",
      selected: "",
    };
  },
  methods: {
    deleteInfo(data: any) {
      this.$emit("deleteInfoEvent", data);
    },
    toActive(data: any) {
      this.$emit("toActiveEvent", data);
    },
    toCompleted(data: any) {
      this.$emit("toCompletedEvent", data);
    },
    toHasDueDate(data: any) {
      this.$emit("toHasDueDateEvent", data);
    },
    toFilterEvent(data: any) {
      console.log(data.filterSelect, "123");
    },
  },
  computed: {
    filterInfo() {
      const oppsitethat = this;
      if (oppsitethat.filterSelect == "All" || oppsitethat.filterSelect == "") {
        return this.listInfo;
      } else {
        return this.listInfo.filter(function (item: any) {
          return item.status == oppsitethat.filterSelect;
        });
      }
    },
  },
});
</script>
<template>
  <div>
    <div class="row p-4 justify-content-end">
      <div class="col-sm-5"></div>
      <div class="col-sm-7 mt-4">
        <div class="row">
          <div
            class="col-auto d-flex align-items-center"
            style="margin-left: 80px"
          >
            <label class="text-secondary">Filter</label>
            <select class="form-select" v-model="filterSelect">
              <option value="" selected>All</option>
              <option value="Completed">Completed</option>
              <option value="Active">Active</option>
              <option value="Has-due-date">Has due date</option>
            </select>
          </div>
          <div class="col-auto d-flex align-items-center px-1 pr-5">
            <label>Sort</label>
            <select class="form-select">
              <option value="added-date-asc" selected>Added date</option>
              <option value="due-date-desc">Due date</option>
            </select>
            <i class="fas fa-sort-amount-down-alt text-info filter-sort"></i>
          </div>
        </div>
      </div>
    </div>
    <div class="row mx-1 px-5 pb-3 w-80">
      <div class="col mx-auto">
        <CompInfo
          v-for="info in filterInfo"
          :key="info.id"
          :info="info"
          @deleteInfo="deleteInfo"
          @toActive="toActive"
          @toCompleted="toCompleted"
          @toHasDueDate="toHasDueDate"
          v-on:toFilterEvent="toFilterEvent"
        />
      </div>
    </div>
  </div>
</template>
<style scoped>
select {
  margin-left: 5px;
}

.filter-sort {
  font-size: 20px;
  margin: 0 20px;
}
</style>
