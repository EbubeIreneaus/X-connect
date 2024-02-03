<template>
    <div>
        <div class="w-full min-h-screen flex items-center justify-center bg-white">
            <div class="max-w-4xl w-full grid grid-cols-2 gap-5 bg-slate-100/50 px-5 rounded">
                <div class="px-5 py-10">
                    <h1 class="font-bold text-xl italic mb-5">X-CONNECT</h1>
                    <p class="text-sm">
                        X-CONNECT, is a global  social networking where businesses
                         and independent professionals connect and collaborate remotely
                    </p>
                </div>
                <div class=" px-5 w-full py-10">
                    <div>
                        <h2 
                        class="text-lg font-semibold relative before:absolute before:w-10 before:h-0.5 py-2
                        before:bg-black/50 before:bottom-0 mb-5"
                        >Sign In</h2>
                    </div>
                    <div>
                        <form>
                            <div class="border px-1.5 flex items-center mb-5">
                                <i class="fa fa-user mx-1.5"></i>
                                <input type="text" placeholder="username" class="outline-0 py-2 w-full ps-2">
                            </div>
                            <div class="border px-1.5 flex items-center mb-7">
                                <i class="fa fa-lock mx-1.5"></i>
                                <input type="password" placeholder="password" class="outline-0 py-2 w-full ps-2">
                            </div>
                            <div class="flex justify-between mb-5">
                                <div>
                                    <input type="radio" id="rememberme">
                                    <label for="rememberme" class="text-sm font-semibold">Remember me</label>
                                </div>
                                <div>
                                    <nuxt-link to="" class="text-sm font-semibold">Forget password?</nuxt-link>
                                </div>
                            </div>
                            <button class="px-10 py-2.5 border bg-black/30 rounded mb-5">
                                sign in
                            </button>

                            <p class="font-semibold text-center mb-5">Login with social media account</p>
                            <button type="button" class="border max-w-lg w-full py-1.5 bg-blue-800 rounded text-white mb-5">
                                <i class="fab fa-facebook-f"></i> &nbsp;
                                <span>facebook</span>
                            </button>
                            <button type="button" class="border max-w-lg w-full py-1.5 bg-blue-800 rounded text-white mb-5">
                                <i class="fa-brands fa-twitter"></i> &nbsp;
                                <span>twitter</span>
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">

</script>

<style scoped>

</style>