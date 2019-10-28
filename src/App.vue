<template>
    <div id="app">
        <Header :cart="cart"/>
        <ItemPage :items="items" :toggle-item="toggleItem"/>
    </div>
</template>

<script>
    import ItemPage from './components/ItemPage.vue'
    import Header from './components/Header.vue'
    import Cart from './models/Cart'
    import Item from './models/Item'

    export default {

        name: 'app',
        data: () => {
            let mainItem = new Item(
                "Programming books bundle",
                50.0,
                "./images/image1.jpg",
                [
                    "./images/image1.jpg",
                    "./images/image2.jpg",
                    "./images/image3.jpg",
                    "./images/image4.jpg"
                ]
            );
            return {
                cart: new Cart(),
                items: [
                    mainItem,
                    new Item("Java Programming", 23.0, "./images/image5.jpg"),
                    new Item("Programming in C++", 15.0, "./images/image6.jpg"),
                    new Item("Programming and fundamentals of Python", 5.50, "./images/image7.jpg"),
                    new Item("My first coding book", 10.90, "./images/image8.jpg")
                ]
            }
        },
        methods: {
            toggleItem: function(id) {
                let index = this.cart.selected.indexOf(id);

                if (index > -1) {
                    this.cart.selected.splice(index, 1);
                    return false;
                }

                this.cart.selected.push(id);
                return true;
            }
        },
        components: {
            ItemPage,
            Header,
        }
    }
</script>

<style>
    * {
        font-family: 'Open Sans', sans-serif;
    }

    html, body {
        margin: 70px 0 0 0;
        padding: 0;
        background-color: #f7f7f7;
    }
</style>
