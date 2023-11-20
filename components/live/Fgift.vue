<script>
const dom = weex.requireModule('dom')
export default {
    data () {
        return {
            defaultAvatar: '/static/demo/1.jpg',
            gifts: []
        }
    },
    methods: {
        // 将礼物置于底部
        toBottom () {
            this.$nextTick(() => {
                // 找到目前最后一个元素，滚动至视图
                let index = this.gifts.length - 1
                let ref = 'item' + index
                if (this.$refs[ref]) {
                    dom.scrollToElement(this.$refs[ref][0], {})
                }
            })
        },
        send (gift) {
            this.gifts.push(gift)
            this.toBottom()
            this.autoHide()
        },
        removeGiftsByIndex (index) {
            if (this.$refs['item' + index]) {
                this.gifts.splice(index, 1)
            }
        },
        // 礼物自己消失
        autoHide () {
            // 找到目前第一个元素，设置定时后移除
            setTimeout(() => this.removeGiftsByIndex(0), Math.round(Math.random() * 300) + 2000)
        }
    }
}
</script>

<template>
    <list style="height: 500rpx;" :show-scrollbar="false" :bounce="false">
        <cell class="flex align-center px-2 pt-2" v-for="(item, index) in gifts" :key="item" insert-animation="default" delete-animation="default" :ref="'item' + index">
            <view class="flex rounded-circle" style="width: 325rpx;background: linear-gradient(to right, #9fe1fa, #f4edc9);">
                <view class="p">
                    <image :src="item.avatar || defaultAvatar" style="width: 70rpx;height: 70rpx;" mode="aspectFill" class="rounded-circle"></image>
                </view>
                <view class="flex-1 flex flex-column justify-center">
                    <text class="text-white font">{{ item.username }}</text>
                    <text class="text-white font-sm">送{{ item.giftName }}</text>
                </view>
                <view class="p">
                    <image :src="item.giftImage" style="width: 70rpx;height: 70rpx;" class="rounded-circle"></image>
                </view>
            </view>
            <text class="text-warning font-lg ml-1">×{{ item.num }}</text>
        </cell>
    </list>
</template>

<style scoped>

</style>
