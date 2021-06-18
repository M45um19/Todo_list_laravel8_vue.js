<template>
    <div>
        <div v-for="(work, index) in works" :key="index">
            <work-list :work= "work" class="work"
            
            v-on:itemchanged="$emit('reloadlist')"

            />
            
        </div>
        
    </div>
</template>

<script>
import workList from './workList.vue'

export default {
    props: ['works'],
    components: {
        workList
    }

}
</script>

<style>
    .work{
        width: 100%;
        margin-bottom: 5px;
    }
</style>