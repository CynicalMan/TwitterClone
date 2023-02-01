<template>
    <div class="w-1/2 h-full overflow-y-scroll">
        <div class="px-5 py-3 border-b border-lighter flex items-center justify-between">
            <h1 class="text-xl font-bold">Home</h1>
            <i class="far fa-star text-xl text-blue"></i>
        </div>
        <div class="px-5 py-3 border-b-8 border-lighter flex">
            <div class="flex-none">
                <img src="propic.jpg" alt="not found" class="flex-none h-12 w-12 rounded-full border border-lighter">
            </div>
            <form v-on:submit.prevent="addNewTweet" class="w-full px-4 relative">
                <textarea v-model="tweet.content" placeholder="What's up?" class="mt-3 pb-3 w-full focus:outline-none"/>
                <div class="flex items-center">
                    <i class="text-lg text-blue mr-4 far fa-image"></i>
                    <i class="text-lg text-blue mr-4 fas fa-film"></i>
                    <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
                    <i class="text-lg text-blue mr-4 far fa-smile"></i>
                </div>
                <button type="submit" class="h-10 px-4 font-semibold text-white bg-blue hover:bg-darkblue rounded-full focus:outline-none absolute bottom-0 right-0">
                    Tweet
                </button>
            </form>
        </div>
        <div class="flex flex-col-reverse">
            <div v-for="tweet in tweets" class="w-full p-4 border-b hover:bg-lighter flex">
                <div class="flex-none mr-4">
                    <img src="propic.jpg" class="h-12 w-12 rounded-full flex-none" />
                </div>
                <div class="w-full">
                    <div class="flex items-center w-full">
                        <p class="font-semibold"> Omar A. Aladly </p>
                        <p class="text-sm text-dark ml-2"> @OaaOmar </p>
                        <p class="text-sm text-dark ml-2"> 1 sec </p>
                        <i class="fas fa-angle-down text-dark ml-auto"></i>
                    </div>
                    <p class="py-2">
                        {{ tweet.content }}
                    </p>
                    <div class="flex items-center justify-between w-full">
                        <div class="flex items-center text-sm text-dark">
                            <i class="far fa-comment mr-3"></i>
                            <p> 0 </p>
                        </div>
                        <div class="flex items-center text-sm text-dark">
                            <i class="fas fa-retweet mr-3"></i>
                            <p> 0 </p>
                        </div>
                        <div class="flex items-center text-sm text-dark">
                            <i class="fas fa-heart mr-3"></i>
                            <p> 1 </p>
                        </div>
                        <div class="flex items-center text-sm text-dark">
                            <i class="fas fa-share-square mr-3"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-for="follow in following" class="w-full p-4 border-b hover:bg-lighter flex">
            <div class="flex-none mr-4">
                <img :src="follow.src" alt="" class="h-12 w-12 rounded-full flex-none">
            </div>
            <div class="w-full ">
                <div class="flex items-center w-full">
                    <p class="font-semibold">{{ follow.name }}</p>
                    <p class="text-sm text-dark ml-2">{{ follow.handle }}</p>
                    <p class="text-sm text-dark ml-2">{{ follow.time }}</p>
                    <i class="fas fa-angle-down text-dark ml-auto"></i>
                </div>
                <p class="py-2">
                    {{ follow.tweet }}
                </p>
                <div class="flex items-center justify-between w-full">
                    <div class="flex items-center text-sm text-dark">
                        <i class="mr-3 far fa-comment"></i>
                        <p>{{ follow.comments }}</p>
                    </div>
                    <div class="flex items-center text-sm text-dark">
                        <i class="mr-3 fas fa-retweet"></i>
                        <p>{{ follow.retweets }}</p>
                    </div>
                    <div class="flex items-center text-sm text-dark">
                        <i class="mr-3 far fa-heart"></i>
                        <p>{{ follow.like }}</p>
                    </div>
                    <div class="flex items-center text-sm text-dark">
                        <i class="mr-3 far fa-share-square"></i>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const following = [
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@teslaBoy', time: '20 min', tweet: 'Should I just quarantine on mars??', comments: '1,000', retweets: '550', like: '1,000,003'},
        {src: 'kevin.jpg', name: 'Kevin Hart', handle: '@miniRock', time: '55 min', tweet: 'Should me and the rock do another sub-par movie together????', comments: '2,030', retweets: '50', like: '20,003'},
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@teslaBoy', time: '1.4 hr', tweet: 'Haha just made a flame thrower. Shld I sell them?', comments: '100,000', retweets: '1,000,002', like: '5,000,003'},
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@teslaBoy', time: '1.4 hr', tweet: 'Just did something crazyyyyyyy', comments: '100,500', retweets: '1,000,032', like: '5,000,103'}
]
const tweets = ref([
    { content: 'It is so nice outside!' }
])
const tweet = ref({ content: '' })

//Methods
const addNewTweet = () => {
    let newTweet = {
        content: tweet.value.content
    }
    tweets.value.push(newTweet)
}

</script>