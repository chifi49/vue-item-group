# Installation
`npm install --save @chifi49/vue-item-group`

or

`<script src="vue-item-group.umd.min.js"></script>`

# Usage
```
<template>
    <vueitemgroup :items="items" @selected_item="selected_item"></vueitemgroup>
</template>
<script>
import vueitemgroup from '@chifi49/vue-item-group'
export default{
    components:{
        vueitemgroup
    },
    data(){
        return {
            items:[
                {
                    text:'Item 1'
                },
                {
                    text:'Item 2'
                },
                {
                    text:'Item 3'
                }
            ]
        }
    },
    methods:{
        selected_item(params){
            console.log(params)
        }
    }
}
</script>
```

# Props
#### items
an array of objects that will show the items

each object need to have a text property with the content that will appear. text property can be html

.e.x
```
[
    {
        text:'Hi there'
    },
    {
        text:'<h1>i m a bigger</h1>'
    }
]
```

#### selected
type: Number

default: -1 (no selected item)

#### toggle_selected
type: Boolean

default: false

when the selected item is clicked it returns selected index to -1 (no item is selected)

#### tag
type: String

default: ul

the html tag wrapper for the items

#### item_tag
type:String 

default: li

the html tag of the item

#### cursor
type:String

default: cursor

the cursor's appearance when item is mouse hovered

#### item_bg_color
type:String (hex, rgb or transparent)

default: #efefef

the item's background color

#### item_selected_bg_color
type:String (hex, rgb or transparent)

default: #6f6f6f

the selected item's background color
#### item_color
type:String (hex, rgb or transparent)

default: #333

the item's color

#### item_selected_color
type:String (hex, rgb or transparent)

default: #fff

the selected item's color

# Events
#### selected_item
Receives as parameter an object with the following properties

oldIndex: the previous selected index (can be -1)

newIndex: the new selected index (can be -1 if we have toggle_selected enabled)

oldItem: the previous selected item (can be undefined)

newItem: the new selected item (can be undefined if we have toggle_selected enabled)