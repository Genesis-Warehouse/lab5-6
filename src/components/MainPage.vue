<template>
    <div class="main-page">
      <div class="sidebar">
        <CategoryList @update-selected-category="updateSelectedCategory"/>  
      </div>
      <div class="content">
        <SortLine
        :sorts="sorts"
        :categoryTitle="selectedCategory.title"
        :selectedSortId="selectedSortId"
        @sort-selected="onSortSelected"
      />
      <PopupWindow :selectedCategory="selectedCategory" :popupSettings="popupSettings" @contentUpdate="contentUpdate" ref="popupRef"></PopupWindow>
      <!-- <StorageItems :items="storageItems" /> -->
        <!-- Остальной контент страницы -->
        <ContentList 
        ref="contentRef" 
        :selectedCategory="this.selectedCategory" 
        @editContent="editContent" 
        @deleteContent="deleteContent" 
        @postNewElement="postNewElement"
        :sortNumber="selectedSortId"
        ></ContentList>
      </div>
    </div>
  </template>
  
  <script>
  import CategoryList from './CategoryList.vue';
  import SortLine from './SortLine.vue';
  // import StorageItems from './StorageItems.vue';
  import ContentList from './ContentList.vue';
  import PopupWindow from './PopupWindow.vue';
  export default {
    name: 'MainPage',
    components: {
      CategoryList,
      SortLine,
      // StorageItems,
      ContentList,
      PopupWindow
    },
    data() {
      return {
        selectedCategory:3,
        popupSettings:{
        changedItem:{},
        ppd:0
      },
        categories: [
          { id: '1', name: 'Продукты' },
          { id: '2', name: 'Партии' },
          { id: '3', name: 'Разделы склада' }
        ],
        sorts: [
          {id:0, name:'Сортировать по:'},
          { id: 1, name: 'Цене' },
          { id: 2, name: 'Дате выпуска' },
          { id: 3, name: 'Сроку годности' }
        ],
        // selectedCategory: { id: '1', title: 'Category 1' },  
        selectedSortId: 0,
      //   storageItems: [
      //   { id: 'item1', name: 'Item 1', details: 'Details for Item 1', isExpanded: false },
      //   { id: 'item2', name: 'Item 2', details: 'Details for Item 2', isExpanded: false },
      //   { id: 'item3', name: 'Item 3', details: 'Details for Item 3', isExpanded: false },
      //   { id: 'item4', name: 'Item 4', details: 'Details for Item 3', isExpanded: false },
      //   { id: 'item5', name: 'Item 5', details: 'Details for Item 3', isExpanded: false }
      // ]
      };
    },
    methods: {
      onSortSelected(sortId) {
        this.selectedSortId = sortId;
        this.contentUpdate();
        // Здесь можно обработать выбор сортировки и выполнить необходимые действия
      },
      updateSelectedCategory(selCat){
        this.selectedCategory=selCat;
      },
      editContent(item){
        this.$refs.popupRef.openPopup();
        this.popupSettings.changedItem=item;
        this.popupSettings.ppd=2;
      },
      deleteContent(item){
        this.$refs.popupRef.openPopup();
        this.popupSettings.changedItem=item;
        this.popupSettings.ppd=3;
      },
      postNewElement(){
        this.$refs.popupRef.openPopup();
        this.popupSettings.ppd=1;
      },
      contentUpdate(){
        this.$refs.contentRef.contentUpdate();
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