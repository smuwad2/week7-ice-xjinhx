<script>

    export default { 
        // Add code in appropriate places
        data() {
            return {
                items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
                inputItem: ""
            }
            
        },
        methods: {removeLi(delItem){
            this.items.splice(delItem,1)
        },
        addLi(){
            this.items.push(this.inputItem) //add new items into the items array
        }
    }
    }
</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
     <ul>
        <li v-for="(item, idx) in items">
            {{item}} <button @click=removeLi(idx)>Delete!</button> <!-- add the delete button and click event, can delete straightaway
            w/o method (check)-->
        </li>
     </ul>

     <input type="text" v-model="inputItem"></input> <button @click=addLi()>Add!</button>
   
</template>
