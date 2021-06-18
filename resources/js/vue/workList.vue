<template>
    <div class="singlework">
        <input type="checkbox" @change="updatework()" v-model="work.completed"/>
        <span :class="[work.completed ? 'completed' : '' , 'work_text' ]" > {{work.work_name}} </span>
        <button @click="removework()" class="remove btn"><i class="fas fa-trash-alt"></i></button>
    </div>
</template>

<script>
export default {
    props: ['work'],
    methods: {
        updatework(){
            axios.put('api/work/'+this.work.id,{
                work:this.work
            }) 
            .then ( response => {
                if(response.status == 200){
                    this.$emit('itemchanged');
                }
            })
            .catch(error => {
                console.log(error);
            })

        },
         removework(){
            axios.delete('api/work/'+this.work.id,{
                work:this.work
            })
            .then ( response => {
                if(response.status == 200){
                    this.$emit('itemchanged');
                }
            })
            .catch(error => {
                console.log(error);
            })
        }
    },
}
</script>

<style>
 .singlework{
     overflow: hidden;
     width: 200%;
     background-color: white;
 
 }
 .completed{
     text-decoration: line-through;
 }
 
 .remove{
     float: right;
     color: red;
 }

     
</style>