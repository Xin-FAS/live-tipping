<script>
export default {
    data () {
        return {
            scrollIntoView: '',
            list: [
                // {
                //     id: 1,
                //     name: '张三',
                //     content: '我发了一段话！'
                // },
                // {
                //     id: 2,
                //     name: '李四',
                //     content: '我发了一段话！'
                // },
                // {
                //     id: 3,
                //     name: '王五',
                //     content: '我发了一段话！'
                // },
            ]
        }
    },
    methods: {
        // 置于底部
        toBottom () {
            setTimeout(() => {
                let len = this.list.length
                if (len > 0 && this.list[len - 1]) {
                    this.scrollIntoView = 'danmu' + this.list[len - 1].id
                }
            }, 200)
        },
        // 发送弹幕
        send (data) {
            this.list.push(data)
            this.toBottom()
        }
    }
}
</script>

<template>
    <view class="bg-warning live-scrolling__warpper">
        <scroll-view :show-scrollbar="false" :scroll-into-view="scrollIntoView" scroll-y
                     style="width: 520rpx;height: 300rpx;" scroll-with-animation class="pl-2">
            <view :id="'danmu' + item.id" v-for="item in list" :key="item.id"
                  class="flex justify-start align-start rounded p-2 mb-2"
                  style="background-color: rgba(255,255,255, .2);">
                <text class="font-md text-danger">{{ item.name }}：</text>
                <text class="font-md text-white">{{ item.content }}</text>
            </view>
        </scroll-view>
    </view>
</template>

<style scoped lang="scss">
// 弹幕
.live-scrolling__warpper {
    position: fixed;
    bottom: 120rpx;
    left: 0;
    right: 0;
}
</style>
