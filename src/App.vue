<script setup>

</script>
<template>
<div class="conteinr">
    <div class="row">
         <div class="col">
              <h1 class="text-left ma-3">зарплате сотрудника</h1>
             <div class="mb-3">
             <label for="name" class="form-label">Ф.И.О. сотрудника </label>
             <input type="text" class="form-control, mx-3" id="name" >
             </div>

             <div class="mb-3">
             <label for="date" class="form-label">Дата выдачи зарплаты  </label>
             <input type="date" class="form-control, mx-3" id="date" >
             </div>


             <div class="mb-3">
             <label for="count" class="form-label">Количество отработанных дней</label>
              <input type="numder" class="form-control, mx-4" id="count" >
             </div>


             <div class="mb-3">
             <label for="price" class="form-label">Размер заработной платы сотрудника</label>
             <input type="namber" class="form-control, mx-3" id="price" >
             </div>

             <button type="button" class="btn btn-dark">добавить</button>

         </div>
    </div>
 </div>
  
</template>

