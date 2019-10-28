<template>
    <div id="app">
        <Header :cart="cart"/>
        <ItemPage :items="items"/>
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
                "image1.jpg",
                [
                    "image1.jpg",
                    "image2.jpg",
                    "image3.jpg",
                    "image4.jpg"
                ]
            );
            return {
                cart: new Cart(),
                items: [
                    mainItem,
                    new Item("Java Programming", 23.0, "image5.jpg"),
                    new Item("Programming in C++", 15.0, "image6.jpg"),
                    new Item("Programming and fundamentals of Python", 5.50, "image7.jpg"),
                    new Item("My first coding book", 10.90, "image8.jpg")
                ]
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
