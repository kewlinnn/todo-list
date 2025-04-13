<template>
  <div class="background">
    <div class="modal-container">
      <h2>Confirm Delete?</h2>
      <p>Are you sure you want to delete this task {{ itemIndex }}?</p>
          <div class="group-btn">
            <button class="confirm-btn btn" @click="$emit('confirm', itemIndex)">Confirm</button>
            <button class="cancel-btn btn" @click="$emit('close')">Cancel</button>
          </div>
    </div>
  </div>
  
</template>

<script setup>
defineProps({
  itemIndex: Number
})
</script>

<style scoped>
.background {
  height: 100vh;
  width: 100%;
  background: rgba(255, 255, 255, 0.267);
  padding: 0;
  margin: 0;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-container {
  background-color: white;
  padding: 1rem;
  border-radius: 5px;
}
h2, p {
  color: black;
}
.group-btn {
  margin-top: 5px;
}
.btn {
  padding: 0.5rem;
  float: right;
  color: white;
  border: none;
  border-radius: 5px;
}
.cancel-btn {
  background-color: grey;
  margin-right: 5px;
}
.confirm-btn {
  background: tomato;
}
</style>