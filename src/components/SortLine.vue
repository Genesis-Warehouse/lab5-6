<template>
    <div class="sort-line">
      <h2 class="sort-line-title">{{ categoryTitle }}</h2>
      <div class="sort-line-sorts">
        <button
          v-for="sort in sorts"
          :key="sort.id"
          class="sort-line-sort"
          @click="selectSort(sort)"
          :class="{ 'sort-line-sort-active': sort.id === selectedSortId }"
        >
          {{ sort.name }}
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SortLine',
    props: {
      sorts: {
        type: Array,
        required: true
      },
      categoryTitle: {
        type: String,
        required: true
      },
      selectedSortId: {
        type: Number,
        default: 0
      }
    },
    methods: {
      selectSort(sort) {
        this.$emit('sort-selected', sort.id);
      }
    }
  }
  </script>
  
  <style scoped>
  .sort-line {
    background-color: #35495e;
    padding: 0 15px;
    display: flex;
    justify-content:space-around;
    align-items: center;
    padding-left:200px ;
  }
  
  .sort-line-title {
    color: #41B882;
    font-size: 1.5em;
  }
  
  .sort-line-sorts {
    display: flex;
  }
  
  .sort-line-sort {
    color: #41B882;
    background-color: #35495e;
    padding: 8px 12px;
    margin-left: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
  }
  
  .sort-line-sort:hover {
    background-color: #41B882;
    color: #35495e;
  }
  
  .sort-line-sort-active {
    background-color: #41B882;
    color: #35495e;
  }
  </style>