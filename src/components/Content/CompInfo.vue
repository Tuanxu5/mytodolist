<script lang="ts">
import { defineComponent, PropType } from "vue";
export default defineComponent({
    name: "CompInfo",
    props: {
        info: {
            type: Object as PropType<any>,
            default: () => []
        },
        textInputInfo: {
            type: Object,
            default: () => []
        },
    },
    methods: {
        handleDelete(e: object): void {
            var data = {
                id: this.info.id,
            }
            this.$emit('deleteInfo', data);
        },
        handleToActive(): void {
            var data = {
                id: this.info.id,
                status: this.info.status
            }
            this.$emit('toActive', data)
        },
        handleToCompleted(): void {
            var data = {
                id: this.info.id,
                status: this.info.status

            }
            this.$emit('toCompleted', data)
        },
        handletoHasDueDate(): void {
            var data = {
                id: this.info.id,
            }
            this.$emit('toHasDueDate', data)
        }
    }
})
</script>
<template>
    <div>
        <div v-if="info.status == 'Completed'">
            <div class="row info" style="height:90px;">
                <div class="col-sm-10">
                    <div class="row">

                        <div class="info-name">
                            <div><i class="far fa-check-square checkbox-check mt-2"></i>
                            </div>
                            <input type="text" v-bind:value="info.title" disabled>
                        </div>
                    </div>
                </div>
                <div class="info-event col-sm-2">
                    <div>
                        <div style="display: flex;justify-content: right;">
                            <div v-on:click="handletoHasDueDate" class=" event-update"><i class="fas fa-pen"></i></div>
                            <div class="event-delete" v-on:click="handleDelete"><i class="fas fa-trash-alt"></i></div>
                        </div>
                        <div style="display: flex;justify-content: right;;
">
                            <div class="info-circle"><i class="fas fa-info-circle"></i></div>
                            <div class="date-update">28th Jun 2020</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-if="info.status == 'Active'">
            <div class="row info" style="height:90px;">
                <div class="col-sm-10">
                    <div class="row" style="margin-left:-25px">
                        <div class="col-sm-9">
                            <div class="info-name">
                                <div>
                                    <i v-on:click="handleToCompleted" class="far fa-square  checkbox-check mt-2"></i>
                                </div>
                                <input type="text" disabled v-bind:value="info.title">
                            </div>
                        </div>
                        <div class="col-sm-2">
                            <div>
                                <button class="btn-date"><i class="fas fa-hourglass-half"></i>28th Jun 2020</button>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="info-event col-sm-2">
                    <div>
                        <div style="display: flex;justify-content: right;">
                            <div v-on:click="handletoHasDueDate" class=" event-update"><i class="fas fa-pen"></i></div>
                            <div class="event-delete" v-on:click="handleDelete"><i class="fas fa-trash-alt"></i></div>
                        </div>
                        <div style="display: flex;justify-content: right;;
">
                            <div class="info-circle"><i class="fas fa-info-circle"></i></div>
                            <div class="date-update">28th Jun 2020</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-if="info.status == 'Has-due-date'">
            <div class="row info" style="height:90px;">
                <div class="col-sm-10">
                    <div class="row">
                        <div class="info-name">
                            <div>
                                <i v-on:click="handleToActive" class="far fa-square  checkbox-check mt-2"></i>
                            </div>
                            <input type="text" class="bg-white" v-model="info.title">
                        </div>
                    </div>
                </div>
                <div class="info-event col-sm-2">
                    <div>
                        <div style="display: flex;justify-content: right;">
                            <div class=" event-update"></div>
                            <div class="event-delete" v-on:click="handleDelete"><i class="fas fa-trash-alt"></i></div>
                        </div>
                        <div style="display: flex;justify-content: right;">
                            <div class="info-circle"><i class="fas fa-info-circle"></i></div>
                            <div class="date-update">28th Jun 2020</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped>
.btn-date {
    margin-left: 15px;
    border-radius: 5px;
    margin-top: 15px;
    background: #fff;
    border: 1px solid #FFC107;
    width: 200px;
    padding: 15px 0;

}

.btn-date>i {
    margin-right: 15px;
    color: #FFC107;

}

.info-name {
    display: flex;
    padding: 25px;
    font-size: 25px;
}

.info-name i {
    margin-right: 20px;
    color: #0D6EFD;
    font-size: 28px;
}

.info-name>input {
    font-family: MyriadPro-Regular;
    border: none;
    width: 100%;
    background-color: #F8F9FA;
}

.info-event {
    display: none;
    cursor: pointer;
    padding-top: 25px;
}

.info:hover .info-event {
    cursor: pointer;
    display: block;
    visibility: visible !important;
}

.event-update {
    color: #0D6EFD;
    font-size: 15px;
    margin: 0 10px;
    ;
}

.event-delete {
    color: #d52b04;
    font-size: 15px;
    margin: 0 10px;
    ;
}

.info-circle {
    color: #a3a3a3;
    font-size: 20px;
    margin: -4px 10px;
    ;
}
</style>
