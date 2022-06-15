<script>
	import {safeArr} from "./common/js/constant"
	export default {
		globalData: {
			needSafe: false
		},
		onLaunch: function() {
			let that = this;
			console.log('App Launch', this.globalData.needSafe)
			wx.getSystemInfo({
  			success (res) {
					// safeArr.includes(res.model) ? that.globalData.needSafe = true : false
					let aim = res.model;
					for (let i=0; i<safeArr.length; i++) {
						if(aim.indexOf(safeArr[i])>=0) {
							that.globalData.needSafe = true
							return 
						}
					}
				}}
			)
		},
		onShow: function() {
			console.log('App Show', this)
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
