<script lang="ts">
import { defineComponent, ref, PropType } from 'vue';
export default defineComponent({
    props: {
        textInputInfo: {
            type: Object,
            default: () => []
        },
        listInfo: {
            type: Array as any,
            default: () => []
        }
    },
    methods: {
        handleAdd(e: object): void {
            var data = {
                text: this.textInputInfo,
            }
            this.$emit('addInfo', data);
            this.textInputInfo.value = "";
        },
    },
});
</script>
<template>
    <form>
        <div class="row m-1 p-3">
            <div class="col col-11 mx-auto">
                <div
                    class="row bg-white rounded shadow-sm p-2 add-todo-wrapper align-items-center justify-content-center">
                    <div class="col">
                        <input class="form-control form-control-lg border-0  bg-transparent rounded" type="text"
                            placeholder="Add new..." v-model="textInputInfo.value">
                    </div>
                    <div class="col-auto px-0 mx-0 mr-2">
                        <i class=" calendar fas fa-calendar-alt mr-3 fs-12"></i>
                        <input type="reset" class="btn btn-primary" v-on:click="handleAdd" value="Add">
                    </div>
                </div>
            </div>
        </div>
    </form>
    <div class="p-2 mx-4 border-black-25 border-bottom"></div>
</template>
<style scoped>
.calendar {
    margin-right: 15px;
    color: #0D6EFD;
    font-size: 20px;
}
</style>
