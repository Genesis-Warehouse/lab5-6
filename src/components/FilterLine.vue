<template>
    <div class="filter-line">
      <h2 class="filter-line-title">{{ categoryTitle }}</h2>
      <div class="filter-line-filters">
        <button
          v-for="filter in filters"
          :key="filter.id"
          class="filter-line-filter"
          @click="selectFilter(filter)"
          :class="{ 'filter-line-filter-active': filter.id === selectedFilterId }"
        >
          {{ filter.name }}
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'FilterLine',
    props: {
      filters: {
        type: Array,
        required: true
      },
      categoryTitle: {
        type: String,
        required: true
      },
      selectedFilterId: {
        type: String,
        default: ''
      }
    },
    methods: {
      selectFilter(filter) {
        this.$emit('filter-selected', filter.id);
      }
    }
  }
  </script>
  
  <style scoped>
  .filter-line {
    background-color: #35495e;
    padding: 0 15px;
    display: flex;
    justify-content:space-around;
    align-items: center;
    padding-left:200px ;
  }
  
  .filter-line-title {
    color: #41B882;
    font-size: 1.5em;
  }
  
  .filter-line-filters {
    display: flex;
  }
  
  .filter-line-filter {
    color: #41B882;
    background-color: #35495e;
    padding: 8px 12px;
    margin-left: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
  }
  
  .filter-line-filter:hover {
    background-color: #41B882;
    color: #35495e;
  }
  
  .filter-line-filter-active {
    background-color: #41B882;
    color: #35495e;
  }
  </style>