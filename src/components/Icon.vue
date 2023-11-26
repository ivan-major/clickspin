<template>
	<span
		class="icon"
		:class="`size-${size}`"
		v-html="icon"
	/>
</template>

<script>
import icons from '@/icons.js'

export default {
	components: {},
	props: {
		iconName: {
			type: String,
			default: 'box',
		},
		size: {
			type: String,
			default: '',
		},
	},

	computed: {
		icon() {
			let icon = icons[this.iconName]
			if (!icon && import.meta.env.DEV) {
				return ''
			}
			return icon
		},
	},
}
</script>

<style lang="scss">
.icon {
	display: inline-flex;
	height: rem(32);
	font-size: rem(32);
	line-height: 1;

    svg {
        height: 100%;
        width: 100%;
    }

	&.size-logo {
		height: rem(21);
		font-size: rem(21);
	}

	&.size-close {
		height: rem(23);
		font-size: rem(23	);
	}

	&.size-form {
		height: rem(20);
		font-size: rem(20);
	}

	&.size-clickspin {
		height: rem(12.38);
		font-size: rem(12.38);
	}

	&.size-clickspin-form {
		height: rem(16);
		font-size: rem(16);
	}

	&.size-img {
		height: 100%;
		width: 100%;
	}
}

@include desc {
	.icon {
		&.size-logo {
		height: rem(35);
		font-size: rem(35);
	}

	&.size-clickspin {
		height: rem(28);
		font-size: rem(28);
	}
	}
}
</style>
