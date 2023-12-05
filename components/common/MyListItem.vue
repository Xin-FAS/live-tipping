<script>
export default {
    name: "MyListItem",
    props: {
        title: {
            type: String,
            default: ''
        },
        icon: {
            type: String,
            default: ''
        },
        content: {
            type: String,
            default: ''
        },
        showArrow: {
            type: Boolean,
            default: true
        }
    }
}
</script>

<template>
    <view class="flex align-center p-3" @click="$emit('click')" hover-class="bg-light">
        <text :class="icon" class="iconfont mr-1 text-warning" style="font-size: 40rpx;"></text>
        <text class="font-md">{{ title }}</text>
        <view class="ml-auto font">
            <slot></slot>
            <text v-if="showArrow" class="text-muted font ml-2">></text>
        </view>
    </view>
</template>

<style scoped lang="scss">

</style>
