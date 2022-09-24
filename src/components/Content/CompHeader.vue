<script lang="ts">
import CompSearch from "./CompSearch.vue"
export default {
    name: "CompHeader",
    components: {
        CompSearch
    }
};

</script>
<template>
    <div class="row m-1 p-4">
        <div class="col">
            <div class="h1 text-primary text-center mx-auto title-text">
                <div><i class="icon-check fas fa-check-square"></i></div>
                <div><u>My Todo-s</u></div>
            </div>
        </div>
    </div>

</template>
<style scoped>
.icon-check {
    font-size: 50px;
    margin-right: 20px;
    ;
}

.title-text {
    padding: 20px;
    justify-content: center;
    display: flex;
}
</style>
