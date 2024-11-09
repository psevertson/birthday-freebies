<template lang="pug">
QLayout(view="hHh lpr lFf")
	QHeader(elevated)
		QToolbar
			QBtn(v-if="$q.screen.lt.md" flat dense round icon="menu" ariaLabel="Menu" @click="toggleLeftDrawer")
			QToolbarTitle Birthday Freebies

	QDrawer.bg-grey-2(v-model="leftDrawerOpen" showIfAbove bordered)
		QList(separator)
			QItem(clickable target="_blank" href="https://github.com/psevertson")
				QItemSection(avatar)
					QIcon(name="person")
				QItemSection
					QItemLabel(caption) Created By
					QItemLabel Porter Severtson
			QItem(clickable target="_blank" href="https://github.com/psevertson/birthday-freebies/issues")
				QItemSection(avatar)
					QIcon(name="feedback")
				QItemSection
					QItemLabel Submit Feedback

	QPageContainer
		IndexPage
</template>

<script setup lang="ts">
import { ref } from "vue"
import IndexPage from "src/pages/IndexPage.vue"

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
	leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
