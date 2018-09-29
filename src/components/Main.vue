<template>
    <div>
        <page-header :changeScreen="changeScreen"></page-header>
        <front-page v-if="page === 'front'"></front-page>
        <win-calculate v-else-if="page === 'win'" class="win-calc"></win-calculate>
        <summary-page v-else></summary-page>
    </div>
</template>
<script>
import PageHeader from "./PageHeader";
import WinCalculate from "./WinCalculate";
import FrontPage from "./FrontPage";
import SummaryPage from "./SummaryPage";
export default {
    data() {
        return {
            page: "front"
        }
    },
    components: {
        PageHeader,
        WinCalculate,
        FrontPage,
        SummaryPage
    },
    methods: {
        changeScreen(page) {
            if (page === "win") {
                this.page = "win";
            } else if (page === "summary") {
                this.page = "summary";
            } else {
                this.page = "front";
            }
        }
    }
}
</script>
<style scoped>
</style>
