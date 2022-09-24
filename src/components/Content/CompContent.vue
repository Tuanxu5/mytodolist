<script lang="ts">
import { defineComponent, PropType } from "vue";
import CompListInfo from "./CompListInfo.vue"

import CompSearch from "./CompSearch.vue"
export default defineComponent(
    {
        name: "CompContent",
        components: {
            CompSearch,
            CompListInfo,
        },
        data() {
            return {
                listInfo: [
                    { id: "1", title: "Buy groceries for next week", status: "Completed" },
                    { id: "2", title: "Renew car insurance", status: "Active" },
                    { id: "3", title: "Sign up for online course", status: "Has-due-date" },
                ],
                Filter: '',
            }
        },
        created() {
            this.listInfo
        },
        methods: {
            handleDeleteInfo(data: any): void {
                var indexDeleteInfo = -1;
                this.listInfo.forEach((i, idx) => {
                    if (i.id == data.id) {
                        indexDeleteInfo = idx;
                        if (indexDeleteInfo != -1) {
                            this.listInfo.splice(indexDeleteInfo, 1);
                        }
                    }
                });
            },
            addInfo(data: any) {
                if (data.text.value == "" || data.text.value == null) {
                    alert("Hehe có mỗi việc nhập vào cũng không biết");
                }
                else {
                    const lenghtList: any = this.listInfo.length;
                    this.listInfo.push({ id: lenghtList + 1, title: data.text.value, status: "Has-due-date" });
                }
            },
            handleToActiveEvent(data: any) {
                this.listInfo[(data.id) - 1].status = "Active"
            },
            handleToCompletedEvent(data: any) {
                this.listInfo[(data.id) - 1].status = "Completed"
            },
            toHasDueDateEvent(data: any) {
                this.listInfo[(data.id) - 1].status = "Has-due-date"
            },
            toFilterEvent(data: any) {
                console.log(this.listInfo.filter(
                    function (item) {
                        return item.status == data.filterSelect
                    }));
            }
        },
    }
)
</script>
<template>
    <CompSearch v-on:addInfo="addInfo" />
    <CompListInfo v-bind:listInfo="listInfo" v-on:deleteInfoEvent="handleDeleteInfo"
        v-on:toActiveEvent="handleToActiveEvent" v-on:toCompletedEvent="handleToCompletedEvent"
        v-on:toHasDueDateEvent="toHasDueDateEvent" />
</template>
<style scoped>
select {
    margin-left: 30px;
}
</style>
