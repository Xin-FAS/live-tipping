<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
            // 加载字体库
            const domModule = weex.requireModule('dom')
            domModule.addRule('fontFace',{
                'fontFamily': 'iconfont-unicode',
                'src': "url('http://at.alicdn.com/t/c/font_4324186_a4a1qph03st.ttf?t=1699536868762')"
            })
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
@import "common/common.css";
@import "common/free.css";
@import "common/icon.css";
</style>
