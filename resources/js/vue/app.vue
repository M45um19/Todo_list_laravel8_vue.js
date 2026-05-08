<template>
<div>    
    <div class="">
        <div class="row">
            <div class="col-sm">
            
            </div>
            <div class="col-sm">
                <br>
                <h3 class="bg-white text-primary p-2 text-center rounded">Todo List</h3>
                <hr>
                <add-work-form
                
                v-on:reloadlist="getwork()"
                
                />
                <br>
                <work-view :works="works"
                
                v-on:reloadlist="getwork()"
                
                />
            </div>
            <div class="col-sm">
            
        </div>
    </div>
</div>
        
    </div>
</template>

<script>

import addWorkForm from './addWorkForm.vue'
import workView from './workView.vue'
export default {
    components: {
            addWorkForm,
            workView
        },
        data: function() {
            return {
                works: []
            }
        },
        methods: {
            getwork(){
                axios.get('/api/works')
                .then(response =>{
                    this.works = response.data
                })
                .catch(error =>{
                    console.log(error)
                })
            }
        },
        created() {
            this.getwork();
        }
}
</script>

<style>

</style>