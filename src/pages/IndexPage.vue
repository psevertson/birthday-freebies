<template lang="pug">
QPage
	.scroll-y.absolute-full.q-py-md.column.no-wrap.q-gutter-y-md.items-center
		template(v-for="row in data" :key="row.name")
			QCard.q-pa-sm(bordered style="width: 500px; max-width: 90vw")
				QCardSection
					.text-h6 {{ row.name }}
					.text-subtitle2.text-grey-8 {{ row.freebie }}
				QSeparator(inset)
				//- QCardSection Valid: {{ row.valid }}
				QCardActions
					QBtn(flat icon="sym_o_event" label="B-Day Only")
					QBtn(flat :icon="requirementIcon(row)" :label="requirementLabel(row)")
</template>

<script setup lang="ts">
import data from "../../public/freebies.json"

function requirementIcon(row: (typeof data)[number]) {
	switch (row.requirement) {
		case "identification":
			return "sym_o_id_card"
		case "app":
			return "sym_o_app_shortcut"
		case "email":
			return "sym_o_mail"
		default:
			return "sym_o_warning"
	}
}
function requirementLabel(row: (typeof data)[number]) {
	switch (row.requirement) {
		case "identification":
			return "ID"
		case "app":
			return "App Signup"
		case "email":
			return "Email Signup"
		default:
			return "Unknown"
	}
}
</script>
