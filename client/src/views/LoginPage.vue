<script>
import { useAuctionStore } from "../stores/auction.js";
import { mapActions } from "pinia";
export default {
  data() {
    return {
      user: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    ...mapActions(useAuctionStore, ["postLogin", "postLoginGoogle"]),
    handleSubmitButton() {
      this.postLogin(this.user);
    },
  },
};
</script>

<template>
  <div>
    <main>
      <router-view></router-view>
      <section class="absolute w-full h-full">
        <div
          class="absolute top-0 w-full h-full bg-gray-300"
          style="background-size: 100%; background-repeat: no-repeat"
          :style="{ backgroundImage: 'url(' + background + ')' }"
        ></div>
        <div class="container mx-auto px-4 h-full">
          <div class="flex content-center items-center justify-center h-full">
            <div class="w-full lg:w-4/12 px-4">
              <div
                class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded-lg bg-gray-100 border-0"
              >
                <div class="rounded-t mb-0 px-6 py-6">
                  <div class="text-center mb-3">
                    <h6 class="text-gray-600 text-sm font-bold">
                      Sign in with
                    </h6>
                  </div>
                  <div class="btn-wrapper text-center flex justify-center">
                    <a
                      href="https://github.com/login/oauth/authorize?client_id=de19d23718b971b968cc"
                      class="bg-white active:bg-gray-100 text-gray-800 px-4 py-2 rounded outline-none focus:outline-none mr-2 mb-1 uppercase shadow hover:shadow-md inline-flex items-center font-bold text-xs"
                      style="transition: all 0.15s ease 0s"
                    >
                      <img
                        alt="..."
                        class="w-5 mr-1"
                        src="../assets/img/github.svg"
                      />Github
                    </a>
                  </div>
                  <hr class="mt-6 border-b-1 border-gray-400" />
                </div>
                <div class="flex-auto px-4 lg:px-10 py-10 pt-0">
                  <div class="text-gray-500 text-center mb-3 font-bold">
                    <small>Or sign in with credentials</small>
                  </div>
                  <form @submit.prevent="handleSubmitButton">
                    <div class="relative w-full mb-3">
                      <label
                        class="block uppercase text-gray-700 text-xs font-bold mb-2"
                        for="grid-password"
                        >Email</label
                      ><input
                        v-model="user.email"
                        type="email"
                        class="border-0 px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded text-sm shadow focus:outline-none focus:ring w-full"
                        placeholder="Email"
                        style="transition: all 0.15s ease 0s"
                      />
                    </div>
                    <div class="relative w-full mb-3">
                      <label
                        class="block uppercase text-gray-700 text-xs font-bold mb-2"
                        for="grid-password"
                        >Password</label
                      ><input
                        v-model="user.password"
                        type="password"
                        class="border-0 px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded text-sm shadow focus:outline-none focus:ring w-full"
                        placeholder="Password"
                        style="transition: all 0.15s ease 0s"
                      />
                    </div>
                    <div>
                      <label class="inline-flex items-center cursor-pointer"
                        ><input
                          id="customCheckLogin"
                          type="checkbox"
                          class="form-checkbox border-0 rounded text-gray-800 ml-1 w-5 h-5"
                          style="transition: all 0.15s ease 0s"
                        /><span class="ml-2 text-sm font-semibold text-gray-700"
                          >Remember me</span
                        ></label
                      >
                    </div>
                    <div class="text-center mt-6">
                      <button
                        class="bg-gray-900 text-white active:bg-gray-700 text-sm font-bold uppercase px-6 py-3 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full"
                        type="submit"
                        style="transition: all 0.15s ease 0s"
                      >
                        Sign In
                      </button>
                      <div class="divider">OR</div>
                      <router-link
                        to="/register"
                        class="bg-blue-900 text-white active:bg-blue-600 text-sm font-bold uppercase px-6 py-3 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full"
                        type="button"
                        style="transition: all 0.15s ease 0s"
                      >
                        Sign Up
                      </router-link>
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>
