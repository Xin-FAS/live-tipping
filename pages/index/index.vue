
<script>
export default {
    data() {
        return {
            title: 'Hello1'
        }
    },
    onLoad() {

    },
    methods: {
        toLive () {
            uni.navigateTo({
                url: '../live/index'
            })
        }
    }
}
</script>

<template>
    <view class="content">
        <!-- 轮播图部分 -->
        <swiper
            indicator-dots
            autoplay
            :interval="3000"
            :duration="1000"
            style="width: 750rpx;height: 250rpx"
        >
            <swiper-item v-for="item in 3" :key="item">
                <view>
                    <image src="../../static/logo.png" mode="aspectFit" style="width: 750rpx;height:250rpx;" />
                </view>
            </swiper-item>
        </swiper>
        <!-- 列表部分 -->
        <view class="flex flex-wrap">
            <view class="list-item" v-for="item in 8" @click="toLive">
                <image src="../../static/logo.png" class="rounded"  mode="aspectFill" />
                <view class="abs-base left-t">
                    <text class="iconfont icon-jinbi1"></text>
                    <text class="text-white" style="margin-left: 10rpx">0</text>
                </view>
                <view class="abs-base right-t">
                    <text>热度：</text>
                    <text>0</text>
                </view>
                <view class="abs-base left-b">
                    <text>标题</text>
                </view>
                <view class="abs-base right-b">
                    <text class="running">直播中</text>
                </view>
            </view>
        </view>
    </view>
</template>

<style scoped lang="scss">
.list-item {
    position: relative;
    box-sizing: border-box;
    padding: 5rpx;
    width: 375rpx;
    height: 375rpx;

    .abs-base {
        position: absolute;
        display: flex;
        align-items: center;
        padding: 0 15rpx;
        border-radius: 30rpx;
        background-color: rgba(0,0,0,.4);
        font-size: 25rpx;
        color: white;
    }

    image {
        width: 365rpx;
        height: 365rpx;
    }

    .left-t {
        left: 15rpx;
        top: 15rpx;
    }
    .right-t {
        top: 15rpx;
        right: 15rpx;
    }
    .left-b {
        left: 15rpx;
        bottom: 15rpx;
    }
    .right-b {
        right: 15rpx;
        bottom: 15rpx;
    }
    .running {
        display: flex;
        align-items: center;

        &::before {
            content: "";
            display: block;
            width: 15rpx;
            height: 15rpx;
            background-color: #3595ff;
            border-radius: 50%;
            margin-right: 5rpx;
        }
    }
}
</style>
