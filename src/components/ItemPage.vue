<template>
    <section>
        <div id="item-container">
            <div class="gallery">
                <img id="item-main-image" :src="items[0].image">
                <div class="thumbnails">
                    <img v-for="(image, index) in items[0].thumbnails" :src="image" :key="index"
                         @click="changeThumbnail(index)">
                </div>
            </div>
            <h1>{{items[0].title}} - {{items[0].price}}$</h1>
            <AddToCart :index="0" :toggle-item="toggleItem"/>
            <Comments/>
        </div>

        <div class="suggested-container">
            <h3>Total: <span id="total-price">{{abc.total}}</span>$</h3>
            <h3>Similar items</h3>
            <ul>
                <li v-for="(item, index) in items" :key="index">
                    <div v-if="index !== 0">
                        <img :src="item.image">
                        <h4>
                            <a href="#">{{item.title}} - {{item.price}}$</a>
                        </h4>
                        <AddToCart :index="index" :toggle-item="toggleItem"/>
                    </div>
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    import AddToCart from './AddToCart'
    import Comments from './Comments'

    export default {
        name: 'ItemPage',
        components: {
            AddToCart,
            Comments
        },
        methods: {
            changeThumbnail: function(index) {
              this.items[0].image = this.items[0].thumbnails[index]
            }
        },
        props: {
            items: Array,
            abc: Object,
            toggleItem: Function
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    section {
        display: flex;
        width: 80%;
        margin: 30px auto;
    }

    section div#item-container {
        flex-grow: 10;
    }

    section div.suggested-container {
        flex-grow: 2;
    }
    #item-main-image {
      height: 400px;
    }

    #item-container h1 {
        margin: 15px 15px;
    }

    #item-container .gallery {
        text-align: center;
    }

    #item-container .thumbnails img {
        width: 100px;
        height: 100px;
        object-fit: cover;
        object-position: top center;
        float: left;
        margin-right: 20px;
        cursor: pointer
    }

    #item-container .thumbnails img:hover {
        cursor: pointer;
        opacity: .7;
    }

    #item-container .thumbnails::after {
        display: block;
        content: "";
        clear: both;
    }

    .suggested-container h3 {
        margin: 15px;
        padding: 15px;
        color: #ffffff;
        background-color: #455a64;
    }

    .suggested-container ul {
        margin: 15px;
        padding: 0;
    }

    .suggested-container ul li {
        list-style: none;
    }

    .suggested-container ul li div {
        margin: 20px 0;
    }

    .suggested-container ul li img {
        width: 20%;
        height: 150px;
        object-fit: cover;
        object-position: top center;
        float: left;
        margin-right: 20px;
    }

    .suggested-container ul li div::after {
        content: "";
        display: block;
        clear: both;
    }

    .suggested-container ul li h4 {
        margin-top: 0;
        margin-bottom: 10px;
    }

    .suggested-container ul li h4 a {
        color: #1a1a1a;
        text-decoration: none;
    }

    .suggested-container ul li h4 a:hover {
        color: #ff5f52;
        text-decoration: underline;
    }

    .suggested-container ul li small {
        color: #bcbcbc;
    }

    footer {
        color: #cccccc;
        text-align: center;
    }

    @media screen and (max-width: 768px) {
        section {
            flex-direction: column;
        }
    }
</style>
