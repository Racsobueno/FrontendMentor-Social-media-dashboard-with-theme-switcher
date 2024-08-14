<template>
  <div id="app">
    <AppHeader></AppHeader>
    <OverviewContainer :overviewItems="overviewItems"></OverviewContainer>
    <OverviewTodayContainer :overviewTodayItems="overviewTodayItems"></OverviewTodayContainer>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import OverviewContainer from './components/OverviewContainer.vue'
import OverviewTodayContainer from './components/OverviewTodayContainer.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    OverviewContainer,
    OverviewTodayContainer
  },
  data() {
      return {
          overviewItems: [],
          overviewTodayItems: []
      }
  },
  mounted() {
      this.fetchJsonData();
  },
  methods:{
      async fetchJsonData() {
        try {
            const response = await fetch('/data/data.json');
            const data = await response.json();

            this.overviewItems = data.overview;
            this.overviewTodayItems = data["overview-today"];

        } catch (error) {
            console.error('Error fetching JSON:', error);
        }
      }
    }
}
</script>

<style scoped>

</style>