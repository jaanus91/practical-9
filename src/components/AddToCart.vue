<template>
    <button :class="{'add-to-cart' : !selected, 'remove-from-cart' : selected}" @click="selected = toggleItem(index)">
        <span v-if="!selected">Add to cart</span>
        <span v-else>Remove from cart</span>
    </button>
</template>

<script>
    export default {
        name: 'AddToCart',
        data: () => {
            return {
                selected: false
            }
        },
        props: {
            index: Number,
            toggleItem: Function
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .add-to-cart {
        padding: 10px;
        color: #ffffff;
        background-color: #455a64;
        border: 1px solid #35444d;
        border-radius: 3px;
    }

    .add-to-cart:hover {
        cursor: pointer;
        border: 1px solid #455a64;
    }

    .remove-from-cart {
        padding: 10px;
        color: #ffffff;
        background-color: #642027;
        border: 1px solid #341114;
        border-radius: 3px;
    }

    .remove-from-cart:hover {
        cursor: pointer;
        border: 1px solid #642027;
    }
</style>
