<!-- File src/App.vue -->
<template>
  <div class="app">
    <h1 class="main-title">{{ title }}</h1>
    <div class="card">
      <HelloUser :name="userName" :class="{highlighted: userName.trim() !== ''}" />
    </div>
    <div class="card">
      <div class="user-picker">
        <p class="user-picker-label">Chọn tên người dùng:</p>
        <div class="user-picker-list">
          <button v-for="user in users" :key="user" @click="userName = user" :class="['user-btn', {active: userName === user}]">{{ user }}</button>
        </div>
      </div>
    </div>
    <div class="card">
      <Slide />
    </div>
    <div class="card">
      <Counter />
    </div>
    <div class="card">
      <SlotExample>
        <template v-slot:header>
          <h2>Tiêu đề do cha định nghĩa</h2>
        </template>
        <p>Nội dung chính ở giữa component con</p>
        <PopUp />
      </SlotExample>
    </div>
  </div>
</template>

<script>
import HelloUser from './components/HelloUser.vue' // Import component HelloUser
import Counter from './components/Counter.vue' // Import component Counter
import FormInput from './components/FormInput.vue' // Import component FormInput
import UserList from './components/UserList.vue' // Import component UserList
import SlotExample from './components/SlotExample.vue' // Import component SlotExample
import Slide from './components/slide.vue'
import PopUp from './components/PopUp.vue'

export default {
  name: 'App',
  components: {
    HelloUser,
    Counter,
    FormInput,
    UserList,
    SlotExample,
    Slide,
    PopUp
  },
  data() {
    return {
      title: 'Title', // Tiêu đề trang
      userName: 'Minh Trí Thành', // Tên người dùng
      users: ['Minh', 'Trí', 'Thành'] // Mảng tên người dùng
    }
  }
}
</script>

<style>
.main-title {
  text-align: center;
  font-size: 2em;
  margin-bottom: 1.5em;
  letter-spacing: 1px;
  font-weight: 800;
  color: #38c6ff;
}
.card {
  margin-bottom: 1.7em;
  text-align: center;
  width: 100%;
  box-sizing: border-box;
}
.main-btn {
  width: 100%;
  font-size: 1.1em;
  padding: 1em 0;
  border-radius: 14px;
  font-weight: 700;
  margin-bottom: 1em;
}
.user-picker {
  width: 100%;
  text-align: center;
  margin-bottom: 0.5em;
}
.user-picker-label {
  font-size: 1.1em;
  font-weight: 700;
  color: #4f8cff;
  margin-bottom: 0.7em;
}
.user-picker-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.7em;
  justify-content: center;
  margin-top: 0.5em;
}
.user-btn {
  background: linear-gradient(90deg, #e0e7ef 0%, #b2d8ff 100%);
  color: #2c3e50;
  border: none;
  border-radius: 12px;
  padding: 0.7em 1.4em;
  font-size: 1.1em;
  font-weight: 700;
  cursor: pointer;
  box-shadow: 0 2px 8px rgba(44,62,80,0.07);
  transition: background 0.2s, color 0.2s, box-shadow 0.2s;
}
.user-btn.active, .user-btn:hover {
  background: linear-gradient(90deg, #4f8cff 0%, #38c6ff 100%);
  color: #fff;
  box-shadow: 0 4px 16px rgba(44,62,80,0.13);
}
@media (max-width: 700px) {
  .main-title {
    font-size: 1.3em;
    margin-bottom: 1em;
  }
  .card {
    margin-bottom: 1.1em;
    padding: 0.7em 0.2em;
  }
  .user-picker-list {
    gap: 0.4em;
  }
  .user-btn {
    font-size: 1em;
    padding: 0.6em 1em;
  }
}
</style>
