<template>
  <div v-if="showPopup" class="popup-overlay">
    <div class="popup">
      <div class="popup-header">
        <span @click="closePopup" class="close-btn">&times;</span>
      </div>
      <div class="popup-content">
        <template v-if="popupSettings.ppd === 3">
          <div class="confirmation-container">
            <p>Вы действительно хотите удалить эту запись?</p>
            <div class="button-container">
              <button @click="deleteItem">Да</button>
              <button @click="closePopup">Нет</button>
            </div>
          </div>
        </template>
        <template v-else>
        <!-- В зависимости от значения selectedCategory отображаем соответствующую форму -->
        <template v-if="selectedCategory === 1">
          <form @submit.prevent="submitEditProductForm" class="form-container">
            <label for="name">Название:</label>
            <input v-model="editedProductItem.name" type="text" id="name" required>
        
            <label for="category">Категория:</label>
            <input v-model="editedProductItem.category" type="text" id="category" required>
        
            <label for="price">Цена:</label>
            <input v-model="editedProductItem.price" type="text" id="price" required>
        
            <label for="production_date">Дата производства:</label>
            <input v-model="editedProductItem.production_date" type="text" id="production_date" placeholder="yyyy-mm-dd" required>
        
            <label for="expiration_date">Срок годности:</label>
            <input v-model="editedProductItem.expiration_date" type="text" id="expiration_date" placeholder="yyyy-mm-dd" required>
        
            <button type="submit">Сохранить</button>
          </form>        
        </template>
        <template v-else-if="selectedCategory === 2">
            <!-- Форма для редактирования branch, когда selectedCategory равен 2 -->
            <form @submit.prevent="submitEditBatchForm">
              <label for="number">Номер:</label>
              <input v-model="editedBatchItem.number" type="text" id="number" required>

              <label for="date">Дата:</label>
              <input v-model="editedBatchItem.date" type="text" id="date" placeholder="yyyy-mm-dd" required>

              <label for="product_id">ID Продукта:</label>
              <input v-model="editedBatchItem.product_id" type="text" id="product_id" required>
              <button type="submit">Сохранить</button>
            </form>
        </template>
        <template v-else-if="selectedCategory === 3">
            <!-- editedWarehouseSections form -->
          <form @submit.prevent="submitEditWarehouseSectionsForm" class="form-container">
            <label for="name">Название:</label>
            <input v-model="editedWarehouseSection.name" type="text" id="name" required>

            <label for="capacity">Вместимость:</label>
            <input v-model="editedWarehouseSection.capacity" type="text" id="capacity" required>

            <label for="condition_id">ID Состояния:</label>
            <input v-model="editedWarehouseSection.condition_id" type="text" id="condition_id" required>

            <button type="submit">Сохранить</button>
          </form>
        </template>
      </template>
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
import axiosConfig from '@/axiosConfig';
export default {
  props: {
    popupSettings: {
      type: Object,
      required: true,
    },
    selectedCategory: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      showPopup: false,
      editedBatchItem: { 
        number:'',
        date:'',
        product_id:''
      }, // Создаем копию объекта product для редактирования
      editedProductItem: { 
      name: '',
      category: '',
      price: '',
      production_date: '',
      expiration_date: ''
      }, // Создаем копию объекта batch для редактирования
      editedWarehouseSection: {
      name: '',
      capacity: '',
      condition_id: ''
}, // Создаем копию объекта warehousesection для редактирования
    };
  },
  methods: {
    openPopup() {
      this.showPopup = true;
    },
    closePopup() {
      this.showPopup = false;
    },
    submitEditProductForm() {
      // Выполните put-запрос через axios с использованием данных из editedItem
      axiosConfig.put(`/products/${this.popupSettings.changedItem.id}`, this.editedProductItem)
        .then(response => {
          console.log('Успешно сохранено', response.data);
          this.closePopup();
        })
        .catch(error => {
          console.error('Ошибка при сохранении', error);
        });
    },
    submitEditBatchForm() {
      // Выполните put-запрос через axios с использованием данных из editedItem
      axiosConfig.put(`/batches/${this.popupSettings.changedItem.id}`, this.editedWarehouseSection)
        .then(response => {
          console.log('Успешно сохранено', response.data);
          this.closePopup();
        })
        .catch(error => {
          console.error('Ошибка при сохранении', error);
        });
    },
    submitEditWarehouseSectionsForm() {
      // Выполните put-запрос через axios с использованием данных из editedItem
      axiosConfig.put(`/warehouse_sections/${this.popupSettings.changedItem.id}`, this.editedBatchItem)
        .then(response => {
          console.log('Успешно сохранено', response.data);
          this.closePopup();
        })
        .catch(error => {
          console.error('Ошибка при сохранении', error);
        });
    },
  },
};
</script>

<style scoped>
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup {
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  max-width: 80%;
  max-height: 80%;
  overflow: auto;
}

.popup-header {
  display: flex;
  justify-content: flex-end;
  padding: 10px;
}

.close-btn {
  cursor: pointer;
  font-size: 20px;
  color: #333;
}

.popup-content {
  padding: 20px;
}

.form-container {
  background-color: #8FB8D6;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 20px;
}

form label {
  display: block;
  margin-bottom: 8px;
  color: #164B70;
}

form input {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  border: 1px solid #75AED;
  border-radius: 4px;
}

form button {
  background-color: #164B70;
  color: #FFFFFF;
  padding: 10px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.confirmation-container {
  background-color: #8FB8D6;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 20px;
}

.confirmation-container p {
  margin-bottom: 16px;
  color: #164B70;
}

.button-container {
  display: flex;
  justify-content: space-between;
}

.button-container button {
  flex: 1;
  background-color: #164B70;
  color: #FFFFFF;
  padding: 10px 16px;
  border: none;
  border-radius: 4px;
  margin-right: 8px;
  cursor: pointer;
}

.button-container button:last-child {
  margin-right: 0;
}
</style>