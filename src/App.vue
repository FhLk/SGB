<script setup>
import { ref } from 'vue';
import Swal from 'sweetalert2'
const persons = ref([
  {
    id: 1,
    name: "Gojo Satoru",
    age: 28,
    pic: "./1.jpg",
    gender: "Male"
  },
  {
    id: 2,
    name: "Maki Zenin",
    age: 20,
    pic: "./2.jpg",
    gender: "Female"
  },
  {
    id: 3,
    name: "Killua Zoldyck",
    age: 20,
    pic: "./3.jpg",
    gender: "Male"
  },
  {
    id: 4,
    name: "Toshiro Hitsugaya",
    age: 25,
    pic: "./4.jpg",
    gender: "Male"
  },
  {
    id: 5,
    name: "Saber Fate",
    age: 28,
    pic: "./5.jpg",
    gender: "Female"
  },
  {
    id: 6,
    name: "Erza Scarlet",
    age: 27,
    pic: "./6.jpg",
    gender: "Female"
  },
  {
    id: 7,
    name: "Edward Elric",
    age: 26,
    pic: "./7.jpg",
    gender: "Male"
  },
  {
    id: 8,
    name: "Loki Atreus",
    age: 21,
    pic: "./8.jpg",
    gender: "Male"
  },
  {
    id: 9,
    name: "Yor Forger",
    age: 26,
    pic: "./9.jpg",
    gender: "Female"
  }
])

const rent = () => {
  Swal.fire({
    title: 'Are you sure?',
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#3085d6',
    cancelButtonColor: '#d33',
    allowOutsideClick: false,
    confirmButtonText: 'Yes'
  }).then((result) => {
    if (result.isConfirmed) {
      loading()
      setTimeout(async() => {
        await Swal.fire(
          "Reservation confirmed.",
          'Have a good day.',
          'success'
        )
      }, 2000)
    }
  })
}

const loading = () => {
  Swal.fire({
    title: "Please Wait",
    allowEscapeKey: false,
    allowOutsideClick: false,
    didOpen: () => {
      Swal.showLoading()
    }
  })

}
</script>
 
<template>
  <div class="p-8">
    <div class="text-center">
      <h1 class="text-3xl font-bold underline my-3">
        SGB Service
      </h1>
      <p>Simulator Girlsfriends and Boyfriends Service</p>
    </div>
    <div class="bg-red-500 p-10 grid grid-cols-3 gap-4 m-3 rounded-lg">
      <div class="card rounded-lg shadow-lg bg-white max-w-sm p-3 mx-3" v-for="(person, index) in persons">
        <div class="bg-[#e5bcbc] p-2 rounded-lg flex justify-center">
          <img :src="person.pic" class="max-w-full h-64 rounded-lg" />
        </div>
        <div class="bg-[#f1e6d0] rounded-lg my-3">
          <p>Name: {{ person.name }}</p>
          <p>Age: {{ person.age }}</p>
          <p>Gender: {{ person.gender }}</p>
        </div>
        <div>
          <button @click="rent()" type="button" class="inline-block px-6 py-2 border-2 border-blue-600 text-blue-600 
            font-medium text-xs leading-tight uppercase rounded hover:bg-black 
            hover:bg-opacity-5 focus:outline-none focus:ring-0 transition 
            duration-150 ease-in-out">
            RENT
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
 
<style scoped>
.card {
  /* width: 30%; */
  text-align: center;
}

.col-4 {
  display: block;
  text-align: center;
}
</style>