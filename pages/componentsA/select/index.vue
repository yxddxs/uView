<template>
	<view class="u-demo">
		<view class="u-demo-wrap">
			<view class="u-demo-title">演示效果</view>
			<view class="u-demo-area">
				<u-select @click="show = true" :default-value="defaultValue" :mode="mode" v-model="show" :list="list" @confirm="confirm"></u-select>
				<view class="u-demo-result-line">select值：{{ result }}</view>
			</view>
		</view>
		<view class="u-config-wrap">
			<view class="u-config-title u-border-bottom">参数配置</view>
			<view class="u-config-item">
				<view class="u-item-title">状态</view>
				<u-subsection vibrateShort :current="current" :list="['打开', '收起']" @change="statusChange"></u-subsection>
			</view>
			<view class="u-config-item">
				<view class="u-item-title">模式</view>
				<u-subsection vibrateShort :list="['单列', '多列独立', '多列联动']" @change="modeChange"></u-subsection>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			show: false,
			result: '尚未选择',
			defaultValue: [3],
			mode: 'single-column', // single-column, mutil-column, mutil-column-auto
			list: [],
			list1: [
				{
					id: '江',
					name: '江'
				},
				{
					id: '湖',
					name: '湖'
				},
				{
					id: '夜',
					name: '夜'
				},
				{
					id: '雨',
					name: '雨'
				},
				{
					id: '十',
					name: '十'
				},
				{
					id: '年',
					name: '年'
				},
				{
					id: '灯',
					name: '灯'
				}
			],
			list2: [
				[
					{
						value: '昔',
						label: '昔'
					},
					{
						value: '去',
						label: '去'
					},
					{
						value: '雪',
						label: '雪'
					},
					{
						value: '如',
						label: '如'
					},
					{
						value: '花',
						label: '花'
					}
				],
				[
					{
						value: '今',
						label: '今'
					},
					{
						value: '来',
						label: '来'
					},
					{
						value: '花',
						label: '花'
					},
					{
						value: '似',
						label: '似'
					},
					{
						value: '雪',
						label: '雪'
					}
				]
			],
			list3: [
				{
					label: '中国',
					value: '1',
					children: [
						{
							label: '广西',
							value: '2',
							children: [
								{
									label: '南宁',
									value: '3'
								},
								{
									label: '梧州',
									value: '3'
								},
								{
									label: '柳州',
									value: '3'
								}
							]
						},
						{
							label: '广东',
							value: '2',
							children: [
								{
									label: '深圳',
									value: '3'
								},
								{
									label: '惠州',
									value: '3'
								},
								{
									label: '清远',
									value: '3'
								}
							]
						}
					]
				},
				{
					label: '美国',
					value: '1',
					children: [
						{
							label: '纽约',
							value: '2',
							children: [
								{
									label: '皇后街道',
									value: '3'
								}
							]
						}
					]
				}
			]
		};
	},
	onLoad() {
		this.list = this.list1;
	},
	computed: {
		current() {
			return this.show ? 0 : 1;
		}
	},
	methods: {
		statusChange(index) {
			this.show = !index;
		},
		modeChange(index) {
			let type = ['single-column', 'mutil-column', 'mutil-column-auto'];
			this.mode = type[index];
			this.list = index == 0 ? this.list1 : index == 1 ? this.list2 : this.list3;
			this.show = true;
		},
		confirm(e) {
			this.result = '';
			e.map((val, index) => {
				this.result += this.result == '' ? val.label : '-' + val.label;
			})
		}
	}
};
</script>

<style scoped lang="scss">
.badge-button {
	padding: 4rpx 6rpx;
	background-color: $u-type-error;
	color: #fff;
	border-radius: 10rpx;
	font-size: 22rpx;
	line-height: 1;
}
</style>
