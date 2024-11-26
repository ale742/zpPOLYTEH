<script setup>
import { ref, computed } from "vue";
const employees = ref([
{
  id: 1,
  name: 'Шекшаев Максим Леонидович',
  date: '24.11.2024',
  count: 20,
  pay: 1000,
  payNalog: 850,
},
{
  id: 2,
  name: 'Иванов Андрей Максимович',
  date: '20.11.2024',
  count: 15,
  pay: 750,
  payNalog: 887.5,
},
{
  id: 3,
  name: 'Летучий Алексей Алексеевич',
  date: '24.11.2024',
  count: 10,
  pay: 500,
  payNalog: 425,
},
]);
const name = ref('');
const date = ref('');
const count = ref('');
const pay = ref('');


const employee = () => {
  if (name.value && date.value && count.value && pay.value) {
    employees.value.push(
      {
  id: Date.now(),
  name: name.value,
  date: (new Date(date.value)).toLocaleDateString(),
  count: count.value,
  pay: pay.value,
}
    );
  }
}

const removeEmp = (id) => {
  employees.value = employees.value.filter((employee) => employee.id != id)
}


</script>

<template>
   <div class="row">
      <div class="col">
        <h1 class="text-center mt-4">Учет заработной платы.</h1>
        <form action="">     
          <div class="mb-3">
            <label for="name" class="form-label">Ф.И.О сотрудника.</label>
            <input type="text" v-model="name" class="form-control" :class="{'is-invalid' : !name}" id="name">
            <div class="invalid-feedback">
       Заполните поле.
      </div>
            </div>
            <div class="mb-3">
            <label for="date" class="form-label">Дата выдачи зарплаты</label>
            <input type="date" v-model="date" class="form-control" :class="{'is-invalid' : !date}" id="date">
            <div class="invalid-feedback">
        Заполните пожалуйста дату.
      </div>
            </div>
            <div class="mb-3">
            <label for="count" class="form-label">Количество отработанных дней </label>
            <input type="number" v-model="count" class="form-control" :class="{'is-invalid' : !count}" id="count">
            <div class="invalid-feedback">
        Заполинте Количество отработанных дней.
      </div>
            </div>
            <div class="mb-3">
            <label for="pay" class="form-label">Размер заработной платы сотрудника</label>
            <input type="number" v-model="pay" class="form-control" :class="{'is-invalid' : !pay}"  id="pay">
            <div class="invalid-feedback">
        Укажите размер заработной платы сотрудника.
      </div>
            </div>
            <div class="mb-3 text-center">
              <button @click="employee" type="button" class="btn btn-outline-danger">Добавить</button>
            </div>
        </form>
      </div>
    </div>




    <div class="row row-cols-1 row-cols-md-3 g-4">
  <div class="col" v-for="employee in employees" :key="employee.id">
    <div class="card h-100">
     
      <div class="card-body">
        <h5 class="card-title">Ф.И.О. сотрудника:</h5>
       <p class="card-text "> {{ employee.name }}</p>
       <h5 class="card-title">Дата выдачи зарплаты:</h5>
        <p class="card-text">{{employee.date}}</p>
        <h5 class="card-title">Количество отработанных дней:</h5>
        <p class="card-text">{{employee.count }}</p>
        <h5 class="card-title">Размер заработной платы сотрудника без налоговых отчислений:</h5>
        <p class="card-text">{{employee.pay}}$</p>
        <h5 class="card-title">Размер заработной платы сотрудника с налоговыми отчислениями (-15%):</h5>
        <p class="card-text">{{ (employee.pay * 0.85).toFixed(2) }}$</p>
      </div>
      <div class="card-footer text-end">
        <button @click="removeEmp(employee.id)" class="btn btn-outline-danger">Удалить</button>
      </div>
    </div>
  </div>
  
    </div>
    <div class="row my-4">
  <div class="col">
    <h3 class="text-end">Общая сумма:</h3>
  </div>
</div>


</template>