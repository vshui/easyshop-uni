<template>
	<view class="modal-box" :class="show?'show':''">
		<view class="dialog">
			<image class="img" :src="thumb" lazy-load mode="widthFix" @tap="posterEvent"></image>
			<text class="cuIcon-roundclose close" @tap="closeEvent"></text>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'modal-img',
		props: {
			thumb: {
				type: String,
				default: ""
			},
			show: {
				type: Boolean,
				default: false
			}
		},
		methods: {
			posterEvent() {
				this.$emit('posterTap');
			},
			closeEvent() {
				this.$emit('posterCloseTap');
			}
		}
	}
</script>

<style lang="scss" scoped>
	.modal-box {
	    position: fixed;
		opacity: 0;
		top: inherit;
		left: inherit;
		right: inherit;
		bottom: inherit;
		z-index: 999999;
	    text-align: center;
	    background: rgba(0, 0, 0, 0.6);
	    transition: all 0.3s;
		pointer-events: none;
		&::before {
		    content: "\200B";
		    display: inline-block;
		    height: 100%;
		    vertical-align: middle;
		}
		.dialog {
			position: relative;
			display: inline-block;
			vertical-align: middle;
			width: 618.18rpx;
			z-index: 999999;
			.img {
				width: 100%;
				border-radius: 3%;
			}
			.close {
			    color: #dadada;
			    top: 18.18rpx;
			    position: relative;
			    font-size: 54.54rpx;	
			}
		}
	}
	.modal-box.show {
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		opacity: 1;
		pointer-events: auto;
	}
</style>
