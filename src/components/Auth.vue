<template>
  <!-- Auth Modal -->
  <div class="fixed z-10 inset-0 overflow-y-auto " id="modal"
  v-if="authModalShow">
    <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center
      sm:block sm:p-0">
      <div class="fixed inset-0 transition-opacity">
        <div class="absolute inset-0 bg-gray-800 opacity-75"></div>
      </div>

      <!-- This element is to trick the browser into centering the modal contents. -->
      <span class="hidden sm:inline-block sm:align-middle sm:h-screen">&#8203;</span>

      <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden
        shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">

        <!-- Add margin if you want to see some of the overlay behind the modal-->
        <div class="py-4 text-left px-6">
          <!--Title-->
          <div class="flex justify-between items-center pb-4">
            <p class="text-2xl font-bold">Your Account</p>
            <!-- Modal Close Button -->
            <div class="modal-close cursor-pointer z-50 " @click.prevent="toggleAuthModal">
              <i class="fas fa-times"></i>
            </div>
          </div>

          <!-- Tabs -->
          <ul class="flex flex-wrap mb-4">
            <li class="flex-auto text-center">
              <a class="block rounded py-3 px-4 transition " href="#" 
                @click.prevent="tab = 'login'" 
                :class="{'hover:text-white text-white bg-blue-600': tab === 'login',
                'hover:text-blue-600':tab==='register'
                }">Login</a>
            </li>
            <li class="flex-auto text-center">
              <a class="block rounded py-3 px-4 transition"
                href="#"  @click.prevent="tab = 'register'"
                :class="{'hover:text-white text-white bg-blue-600': tab === 'register',
                'hover:text-blue-600':tab==='login'
                }">Register</a>
            </li>
          </ul>
          <Login :tab="tab"/>
          <Register :tab="tab"/>

       
          <!-- Registration Form -->

          <!-- validation-schema is used to keep all set of rules in one place -->
        
         
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Login from './Login'
import Register from './Register'
import { computed, ref } from '@vue/runtime-core';
import { useStore } from 'vuex';
import { useForm, useField } from 'vee-validate';
import { Form, Field } from 'vee-validate';
import {mapMutations,mapState} from 'vuex'

export default {
  name: 'Auth',
   components:{
     Login,
     Register
     
    },
  data(){
    return{
      tab:'login',
     

    }
  },
  computed:{
    authModalShow(){
     return this.$store.state.authModalShow
    
    }

  },
  methods:{
   
    toggleAuthModal(){
      this.$store.commit('toggleAuthModel')
    },
  
  }

  // setup() {
  //   const tab = ref('login')

  //    const store = useStore()
  //    const authModalShow = computed(()=>{
  //     return store.getters.authModalSho
  //    })
  //     const isRequired=(value)=> {
  //     return value ? true : 'This field is required';
  //   }
  //   const toggleModal = ()=>{
  //    store.commit('toggleAuthModel')
  // }
  //    return{authModalShow,store,toggleModal,tab,isRequired}
  // }
};
</script>

<style>

</style>
