<template>
<div id="app">
    <vueitemgroup ref="itemgroup" :toggle_selected="true" @selected_item="selectedItem" :items="items" direction="horizontal"></vueitemgroup>
    <br />
    <button @click="$refs['itemgroup'].clearSelection()">clear selection</button>
    <br />
    <button @click="$refs['itemgroup'].selectItem(1);">Select 2nd item</button>
</div>
</template>
<script>
import vueitemgroup from './vue-item-group.vue'
export default{
    components:{
        vueitemgroup
    },
    data(){
        return {
            items:[
                {
                    text:'Button 1'
                },
                {
                    text:'Button 2'
                },
                {
                    text:'Button 3'
                }
            ]
        }
    },
    methods:{
        clearSelection(){

        },
        selectedItem(params){
            console.log(params);
        }
    }
}
</script>