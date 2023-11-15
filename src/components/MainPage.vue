<template>
    <div class="main-page">
      <CategoryList :categories="categories" />
      <FilterLine
        :filters="filters"
        :categoryTitle="selectedCategory.title"
        :selectedFilterId="selectedFilterId"
        @filter-selected="onFilterSelected"
      />
      <StorageItems :items="storageItems" />
      <!-- Остальной контент страницы -->
    </div>
  </template>
  
  <script>
  import CategoryList from './CategoryList.vue';
  import FilterLine from './FilterLine.vue';
  import StorageItems from './StorageItems.vue';
  export default {
    name: 'MainPage',
    components: {
      CategoryList,
      FilterLine,
      StorageItems
    },
    data() {
      return {
        categories: [
          { id: '1', name: 'Category 1' },
          { id: '2', name: 'Category 2' },
          { id: '3', name: 'Category 3' }
        ],
        filters: [
          { id: 'filter1', name: 'Filter 1' },
          { id: 'filter2', name: 'Filter 2' },
          { id: 'filter3', name: 'Filter 3' }
        ],
        selectedCategory: { id: '1', title: 'Category 1' },
        selectedFilterId: '',
        storageItems: [
        { id: 'item1', name: 'Item 1', details: 'Details for Item 1', isExpanded: false },
        { id: 'item2', name: 'Item 2', details: 'Details for Item 2', isExpanded: false },
        { id: 'item3', name: 'Item 3', details: 'Details for Item 3', isExpanded: false },
        { id: 'item4', name: 'Item 4', details: 'Details for Item 3', isExpanded: false },
        { id: 'item5', name: 'Item 5', details: 'Details for Item 3', isExpanded: false }
      ]
      };
    },
    methods: {
      onFilterSelected(filterId) {
        this.selectedFilterId = filterId;
        // Здесь можно обработать выбор фильтра и выполнить необходимые действия
      }
    }
  };
  </script>
  
  <style scoped>
  .main-page {
    display:flexbox;
    justify-content: space-between;
    padding: 0px;
    margin: 0px;
  }
  </style>