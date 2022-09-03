<template>
  <div>
    <v-container>
      <h1 class=" text-center">Home</h1>


      <v-form v-model="valid">

        <v-row>
          <v-col cols="12" md="4">
            <v-text-field v-model="firstName" :rules="nameRules" :counter="10" label="First name" required>
            </v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field v-model="lastName" :rules="nameRules" :counter="10" label="Last name" required></v-text-field>
          </v-col>
        </v-row>

      </v-form>

      {{ getFullName() }}

      <div class="d-flex flex-column justify-space-between align-center">
        <v-img aspect-ratio="16/9" width="300" :src="Data_image" cover></v-img>
      </div>

      <form @submit.prevent="submitForm">

        <v-text-field v-on:input="setNickName" :rules="nameRules" :counter="10" label="ชื่อเล่น" required>
        </v-text-field>
        <div class="fill-height">
          <v-btn block
           color="primary" type="submit">บันทึก</v-btn>
        </div>
      </form>

      <h2>ชื่อเล่น : {{ nickName }}</h2>

      <p>ข้อมูลพื้นฐาน</p>
      <ul>
        <li>เพศ :{{ general.gender }}</li>
        <li>อายุ :{{ age }}</li>
      </ul>

      <v-btn color="primary" @click="showData">ดูข้อมูล</v-btn>

      <v-btn color="secondary" class="mx-1" @click.ctrl="increment(5)">เพิ่ม</v-btn>
      <v-btn color="error" @click.middle="decrement(5)">ลบ</v-btn>


    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      nickName: '',
      age: 25,
      nameRules: [
        v => !!v || 'กรุณากรอกข้อความ ',
        v => v.length <= 10 || 'ข้อความเกิน 10 ตัวอักษร',
      ],
      valid: false,
      Data_image: "https://cdn.vuetifyjs.com/images/parallax/material.jpg",
      general: {
        gender: "ชาย", weight: 100, height: 180, status: false
      },

    }
  },
  methods: {
    getFullName() {
      return `${this.firstName}  ${this.lastName} `
    },
    showData() {
      alert(this.firstName)
    },
    increment(data) {
      this.age = this.age += data
    },
    decrement(data) {
      this.age = this.age -= data
    },
    setNickName(e) {
      this.nickName = e.target.value;

    },
    submitForm(e) {
      e.preventDefault()
      alert('บันทึกชื่อเล่นสำเร็จ !')
    }
  }

}
</script>

<style>
</style>