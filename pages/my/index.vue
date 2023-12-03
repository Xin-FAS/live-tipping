<script>
export default {
    name: "index"
}
</script>

<template>
    <view>
        <view class="flex align-center">
            <view class="flex align-center justify-center" style="width: 180rpx;height: 180rpx;">
                <image src="/static/demo/1.jpg" class="rounded-circle" mode="aspectFill" style="width: 105rpx;height: 105rpx;"></image>
            </view>
            <view class="flex flex-column">
                <text class="font-md">昵称</text>
                <text class="font text-muted">描述</text>
            </view>
            <view class="ml-auto mr-3">
                <view class="border border-main flex justify-center align-center p-2">
                    <text class="text-main font">编辑资料</text>
                </view>
            </view>
        </view>
        <view class="f-divider"></view>
    </view>
</template>

<style scoped>

</style>
