<script setup lang="ts">
import { computed } from 'vue'
import { useGlobalBlock } from '@bagelink/blox'

interface Theme {
	accent?: string
	bg?: string
	ink?: string
	muted?: string
	font_display?: string
	font_body?: string
	radius?: string
}

const { data } = useGlobalBlock<Theme>('SiteTheme')

const css = computed(() => {
	const t = data.value || {}
	const vars: Record<string, string> = {
		'--bgl-primary': t.accent || '#d95f2b',
		'--bgl-bg': t.bg || '#161310',
		'--bgl-font-color': t.ink || '#f3ece2',
		'--bgl-muted': t.muted || '#a89c8e',
		'--bgl-font-display': t.font_display || "'Fraunces', Georgia, serif",
		'--bgl-font': t.font_body || "'Hanken Grotesk', system-ui, sans-serif",
		'--bgl-card-border-radius': t.radius || '20px',
		'--bgl-btn-border-radius': t.radius || '20px',
		'--bgl-input-border-radius': t.radius || '12px',
	}
	return ':root{' + Object.entries(vars).map(([k, v]) => `${k}:${v};`).join('') + '}'
})
</script>

<template>
	<component :is="'style'" v-html="css" />
</template>
