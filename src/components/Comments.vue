<template>
    <div>
        <div class="comment-contents">
            <div class="comment" v-for="(comment, index) in comments" :key="index">
                <div class="commented-at">{{formatDate(comment.createdAt)}}</div>
                {{comment.text}}
            </div>
        </div>
        <div class="comment-box">
            <textarea rows="10" placeholder="Leave a Comment..."
                      @keyup.enter="submit"></textarea>
        </div>
    </div>
</template>

<script>
    import Comment from "../models/Comment";
    export default {
        name: "Comments",
        data: () => {
            return {
                comments: [
                    new Comment("hello"),
                    new Comment("hi")
                ]
            }
        },
        methods: {
            submit : function (event) {
                let comment = new Comment(event.target.value)
                this.comments.push(comment)
                event.target.value = ""
            },
            formatDate: function (date){
                return date.getFullYear()
                    + "/" +
                    date.getMonth()
                    + "/" +
                    date.getDate()
                    + " " +
                    date.getHours()
                    + ":" +
                    date.getMinutes()
            }
        }
    }
</script>

<style scoped>
    .comment-contents {
        margin: 30px 0;
    }

    .comment-contents .comment {
        padding: 15px;
        background-color: #9ED0DB;
        border-radius: 20px;
        margin: 10px 0;
    }
    .comment-contents .comment .commented-at{
        font-size: 10px;
        color: #ffffff;
    }

    .comment-box {
        margin-top: 30px;
    }

    .comment-box textarea {
        width: 100%;
        box-sizing: border-box;
        height: 50px;
        padding: 10px;
        font-size: 12px;
        border: 1px dashed #000000;
        resize: none;
    }
</style>