<template>
    <div class="storage-items">
      <h2 class="storage-items-title">Storage Items</h2>
      <ul class="storage-items-list">
        <li v-for="item in items" :key="item.id" class="storage-item">
          <div class="item-info">
            <span class="item-name">{{ item.name }}</span>
            <button @click="toggleDetails(item)" class="details-button">Expand</button>
          </div>
          <div v-if="item.isExpanded" class="item-details">
            <!-- Вывод дополнительной информации о предмете -->
            {{ item.details }}
          </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StorageItems',
    props: {
      items: {
        type: Array,
        required: true
      }
    },
    methods: {
      toggleDetails(item) {
        item.isExpanded = !item.isExpanded;
      }
    }
  }
  </script>
  
  <style scoped>
  .storage-items {
    background-color: #164B70;
    padding: 15px 300px;
    border-radius: 5px;
  }
  
  .storage-items-title {
    color: #75AED6;
    font-size: 1.5em;
    margin-bottom: 10px;
  }
  
  .storage-items-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .storage-item {
    background-color: #8FB8D6;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .item-info {
    display: flex;
    align-items: center;
  }
  
  .item-name {
    margin-right: 10px;
  }
  
  .details-button {
    background-color: #75AED6;
    color: #164B70;
    border: none;
    padding: 5px 10px;
    border-radius: 3px;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
  }
  
  .details-button:hover {
    background-color: #164B70;
    color: #75AED6;
  }
  
  .item-details {
    margin-top: 10px;
    color: #75AED6;
  }
  </style>