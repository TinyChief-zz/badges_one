<template>
	<section class="galery-page">
		<div class="section-title">
			<h1>
				Галерея значков
			</h1>
		</div>
			
			<Badges></Badges>
	</section>
</template>

<script>
import Badges from '@/pages/galery/components/Badges';
export default {
	components: {
		Badges
	},
	data () {
		return {
			types: [],
			
		}
	}
}
</script>

<style scoped>



</style>
