<template>
    <div>
        <input type="text" class="form-control" v-model="work.name">
        <br>
        <button class="btn bg-white text-primary fw-bolder w-100" @click="addwork()">Add Work</button>
        
    </div>
</template>

<script>
export default {
    data: function () {
        return{
            work: {
                name:""
            }
        }
    },
    methods: {
        addwork() {
            if( this.work.name == ''){
                return;
            }
            axios.post('api/work/store', {
                work: this.work
                
            })
            .then(response =>{
                if(response.status == 201){
                    this.work.name = ""
                    this.$emit('reloadlist');
                    
                    
                }
            })
           
            .catch(error=> {
                console.log(error);
            })
        }
    }  

}
</script>

<style>
    .work_form{
        width: 75%;
    }
</style>