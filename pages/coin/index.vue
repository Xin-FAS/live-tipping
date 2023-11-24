<script>
export default {
    name: "index"
}
</script>

<template>
    <view class="p-3 border-top border-light-secondary">
        <view class="rounded py-4 flex flex-column align-center justify-center bg-main">
            <text class="text-white font-sm mb-2">当前金币</text>
            <text class="text-white font-weight-bold" style="font-size: 60rpx;">500</text>
        </view>
        <view class="border-top border-light-secondary my-3"></view>
        <view>
            <text class="font-sm text-secondary">请选择要充值的金币数量：</text>
        </view>
        <view class="flex flex-wrap" style="margin-left: -20rpx;margin-right: -20rpx;">
            <view class="p-2" style="width: 33.3%;box-sizing: border-box" v-for="item in 6" :key="item">
                <view class="border rounded flex flex-column justify-center align-center" style="height: 130rpx;">
                    <view class="flex align-center">
                        <text style="font-family: iconfont-unicode;">&#xeca0;</text>
                        <text class="font-md font-weight-bold">10</text>
                    </view>
                    <text class="font text-light-muted">￥10</text>
                </view>
            </view>
        </view>
    </view>
</template>

<style scoped lang="scss">

</style>
