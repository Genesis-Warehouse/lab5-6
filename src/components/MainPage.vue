<template>
    <div class="main-page">
      <div class="sidebar">
        <CategoryList :categories="categories"/>  
      </div>
      <div class="content">
        <FilterLine
        :filters="filters"
        :categoryTitle="selectedCategory.title"
        :selectedFilterId="selectedFilterId"
        @filter-selected="onFilterSelected"
      />
      <!-- <StorageItems :items="storageItems" /> -->
        <!-- Остальной контент страницы -->
        <ContentList :selectedCategory="this.selectedCategory"></ContentList>
      </div>
    </div>
  </template>
  
  <script>
  import CategoryList from './CategoryList.vue';
  import FilterLine from './FilterLine.vue';
  // import StorageItems from './StorageItems.vue';
  import ContentList from './ContentList.vue';
  export default {
    name: 'MainPage',
    components: {
      CategoryList,
      FilterLine,
      // StorageItems,
      ContentList
    },
    data() {
      return {
        selectedCategory:3,
        categories: [
          { id: '1', name: 'Продукты' },
          { id: '2', name: 'Партии' },
          { id: '3', name: 'Разделы склада' }
        ],
        filters: [
          { id: '1', name: 'f1' },
          { id: '2', name: 'f2' },
          { id: '3', name: 'f3' }
        ],
        // selectedCategory: { id: '1', title: 'Category 1' },  
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
  .content {
    display:flexbox;
    justify-content: space-between;
    padding: 0px 0px 0px 200px;
    margin: 0px;
  }
  .sidebar{
    width: 200px;
    position: fixed;
    height: 100%;
  }
  </style>