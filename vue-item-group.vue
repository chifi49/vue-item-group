<template>
    <component :is="tag" 
                :style="{'display':direction=='horizontal'?'flex':'auto','list-style':'none','margin':0,padding:0}"
                >
        <component  :key="'item-'+index"
                    :is="item_tag" 
                    v-for="(item,index) in items" 
                    v-html="item.text" 
                    :style="{'margin':0,padding:'5px',borderStyle:'solid','border-color':border_color,'borderTopWidth':'1px','borderBottomWidth':'1px',borderLeftWidth:'1px','borderRightWidth':index==items.length-1?'1px':'0px','cursor':'pointer',
                    'backgroundColor':index==selectedIndex?item_selected_bg_color:item_bg_color,
                    'color':index==selectedIndex?item_selected_color:item_color,
                    'borderTopLeftRadius':index==0?border_radius:'0px',
                    'borderBottomLeftRadius':index==0?border_radius:'0px',
                    'borderTopRightRadius':index==items.length-1?border_radius:'0px',
                    'borderBottomRightRadius':index==items.length-1?border_radius:'0px'}"
                    @click="selectItem(index)"
                    >
        </component><!--item-->
    </component><!--items parent-->
</template>
<script>
export default{
    props:{
        tag:{
            required:false,
            type:String,
            default:'ul'
        },
        item_tag:{
            required:false,
            type:String,
            default:'li'
        },
        items:{
            required:false,
            type:Array,
            default:function(){
                return []
            }
        },
        cursor:{
            type:String,
            default:'pointer',
            required:false
        },
        border_color:{
            type:String,
            default:'#333',
            required:false
        },
        border_radius:{
            type:String,
            default:'5px',
            required:false
        },
        direction:{
            type:String,
            default:'horizontal',
            required:false
        },
        item_bg_color:{
            type:String,
            required:false,
            default:'#efefef'
        },
        item_color:{
            type:String,
            default:'#333'
        },
        item_selected_bg_color:{
            type:String,
            required:false,
            default:'#6f6f6f'
        },
        item_selected_color:{
            type:String,
            required:false,
            default:'#fff'
        },
        toggle_selected:{ //if we click again the selected index, return to opposite state
            type:Boolean,
            required:false,
            default:false
        },
        selected:{
            type:Number,
            required:false,
            default:-1
        }
    },
    data(){
        return {
            selectedIndex: this.selected
        }
    },
    methods:{
        clearSelection(){
            
            this.selectItem(-1);
            
        },
        selectItem(index){
            var previous_index = this.selectedIndex;
            if(previous_index==index && this.toggle_selected){
                this.clearSelection();
            }else if(  previous_index!=index  ){
                this.selectedIndex = index;
                this.$emit('selected_item',{oldIndex:previous_index,newIndex:index,previousItem: this.items[previous_index], newItem: this.items[index]});
            }
        }
    },
    mounted(){
       // console.log(this.direction);
    }
}
</script>