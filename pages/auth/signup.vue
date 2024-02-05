<template>
    <div class="w-full min-h-screen bg-slate-200 border font-serif">
        <div class="border max-w-2xl py-7 mx-auto my-[10%] px-10">
            <div class="mb-4">
                <h2 class="italic font-bold text-2xl">X-CONNECT</h2>
                <p class="text-sm">
                    X-CONNECT, is a global social networking where businesses and
                    independent professionals connect and collaborate remotely
                </p>
            </div>
            <div v-if="comp == 'name'">
                <div class="w-full min-h-[100px] border flex items-center gap-5 px-2">
                    <div class="w-full">
                        <label for="" class="block mx-1">Firstname:</label>
                        <input type="text" v-model="form.firstname" class="outline-none border py-2.5 w-full ps-3" placeholder="Firstname" />
                    </div>
                    <div class="w-full">
                        <label for="" class="block mx-1">Lastname:</label>
                        <input type="text" v-model="form.lastname" class="outline-none border py-2.5 w-full ps-3" placeholder="Lastname" />
                    </div>
                </div>
                <div class="flex justify-end items-center my-5">
                    <button class="border px-10 py-2.5 bg-slate-300" @click="nextReg('name')">
                        next
                    </button>
                </div>
            </div>

            <div v-if="comp == 'user'">
                <div class="w-full min-h-[100px] border flex items-center gap-5 px-2">
                    <div class="w-full">
                        <label for="" class="block mx-1">username:</label>
                        <input type="text" v-model="form.username" class="outline-none border py-2.5 w-full ps-3" placeholder="username" />
                    </div>
                    <div class="w-full">
                        <label for="" class="block mx-1">email:</label>
                        <input type="email" v-model="form.email" class="outline-none border py-2.5 w-full ps-3" placeholder="email" />
                    </div>
                </div>
                <div class="flex justify-between items-center my-5 px-5">
                    <button class="border px-10 py-2.5 bg-slate-300" @click="comp = 'name'">
                        prev
                    </button>
                    <button class="border px-10 py-2.5 bg-slate-300" @click="nextReg('user')">
                        next
                    </button>
                </div>
            </div>

            <div v-if="comp == 'country'">
                <div class="w-full min-h-[100px] border flex items-center gap-5 px-2">
                    <div class="w-full">
                        <label for="" class="block mx-1">country of residence:</label>
                        <input type="text" v-model="form.country" class="outline-none border py-2.5 w-full ps-3" placeholder="country" />
                    </div>
                </div>
                <div class="flex justify-between items-center my-5 px-5">
                    <button class="border px-10 py-2.5 bg-slate-300" @click="comp = 'user'">
                        prev
                    </button>
                    <button class="border px-10 py-2.5 bg-slate-300" @click="nextReg('country')">
                        next
                    </button>
                </div>
            </div>

            <div v-if="comp == 'password'">
                <div class="w-full min-h-[100px] border flex items-center gap-5 px-2">
                    <div class="w-full">
                        <label for="" class="block mx-1">password:</label>
                        <input type="password" id="password" class="outline-none border py-2.5 w-full ps-3"
                            placeholder="password" v-model="form.password" />
                    </div>
                    <div class="w-full">
                        <label for="" class="block mx-1">password:</label>
                        <input type="password" v-model="confirmPass" id="confirm" class="outline-none border py-2.5 w-full ps-3"
                            placeholder="confirm" />
                    </div>
                </div>
                <div class="flex justify-between items-center my-5 px-5">
                    <button class="border px-10 py-2.5 bg-slate-300" @click="comp = 'country'">
                        prev
                    </button>
                    <button class="border px-10 py-2.5 bg-slate-300" @click="nextReg('password')">
                        next
                    </button>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup lang="ts">
import axios from 'axios'
let comp = ref<"name" | "user" | "country" | "password" | "profile">("name");
let validatePassword: () => void;

const confirmPass = ref<string>('')
const form = reactive({
    'firstname': '', 'lastname': '', 'username': '', 'email':'', 'country': '', 'password': ''

})

validatePassword = (): void => {
    const password = document.querySelector("#password") as HTMLFormElement;
    const confirm = document.querySelector("#confirm") as HTMLFormElement;
    if (password.value == confirm.value) {
        comp.value = "profile";
    } else {
        confirm.style.border = "1px solid red";
    }
};


function nextReg(component: "name" | "user" | "country" | "password" | "profile") : void {
    switch (component) {
        case 'name':
            (form.firstname == '' || form.lastname == '')?alert('please fill in your firstname and lastname'): comp.value = 'user'
            break;

        case 'user':
        (form.username == '' || form.email== '')?alert('please fill in your username and email'): comp.value = 'country'
            break;

        case 'country':
            (form.country  =='')?alert('please fill in your country name'): comp.value = 'password'
            break;

        case 'password':
        (form.password == '' || confirmPass.value == '')?alert('please fill in your username and email'): validatePassword()
            break;

        default:
            break;
    }
}

async function register (){
    
    const {data:res, pending, error} = await useFetch('',{
        body: form,
        method: 'post',
        watch: false
    })
}
</script>

<style scoped></style>
