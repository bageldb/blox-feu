<script setup lang="ts">
import SiteHeader from './blocks/SiteHeader.vue'
import SiteFooter from './blocks/SiteFooter.vue'
import ThemeProvider from './ThemeProvider.vue'
</script>

<template>
	<div>
		<ThemeProvider />
		<SiteHeader />
		<main id="content">
			<router-view />
		</main>
		<SiteFooter />
	</div>
</template>
