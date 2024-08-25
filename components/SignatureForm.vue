<template>
    <div class="p-6 max-w-3xl mx-auto">
      <form @submit.prevent="generateSignature" class="bg-white p-6 rounded-lg shadow-lg">
        <h1 class="text-2xl font-bold mb-6">HTML Mail İmzası Oluşturucu</h1>
        <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
          <div>
            <label for="name" class="block text-sm font-medium text-gray-700">Ad:</label>
            <input v-model="form.name" id="name" type="text" required
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="title" class="block text-sm font-medium text-gray-700">Unvan:</label>
            <input v-model="form.title" id="title" type="text" required
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700">E-posta:</label>
            <input v-model="form.email" id="email" type="email" required
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="phone" class="block text-sm font-medium text-gray-700">Telefon:</label>
            <input v-model="form.phone" id="phone" type="tel" required
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="company" class="block text-sm font-medium text-gray-700">Şirket:</label>
            <input v-model="form.company" id="company" type="text" required
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="address" class="block text-sm font-medium text-gray-700">Adres:</label>
            <input v-model="form.address" id="address" type="text"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="website" class="block text-sm font-medium text-gray-700">Web Sitesi:</label>
            <input v-model="form.website" id="website" type="url"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
          <div>
            <label for="logo" class="block text-sm font-medium text-gray-700">Şirket Logosu (URL):</label>
            <input v-model="form.logo" id="logo" type="text"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
          </div>
        </div>
        <button type="submit"
          class="mt-6 px-4 py-2 bg-indigo-600 text-white font-semibold rounded-md shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          İmza Oluştur
        </button>
      </form>
  
      <div v-if="signatureHtml" class="mt-6 bg-white p-6 rounded-lg shadow-lg">
        <h3 class="text-xl font-semibold mb-4">Oluşturulan İmza:</h3>
        <div v-html="signatureHtml" class="border border-gray-200 p-4 rounded-lg"></div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        form: {
          name: '',
          title: '',
          email: '',
          phone: '',
          company: '',
          address: '',
          website: '',
          logo: ''
        },
        signatureHtml: ''
      }
    },
    methods: {
      generateSignature() {
        this.signatureHtml = `
          <div style="font-family: Arial, sans-serif; font-size: 14px;">
            <img src="${this.form.logo}" alt="${this.form.company}" style="max-width: 150px;" /><br />
            <strong>${this.form.name}</strong><br />
            ${this.form.title}<br />
            <a href="mailto:${this.form.email}" style="color: #1d4ed8;">${this.form.email}</a><br />
            Tel: ${this.form.phone}<br />
            ${this.form.company}<br />
            ${this.form.address}<br />
            <a href="${this.form.website}" style="color: #1d4ed8;">${this.form.website}</a>
          </div>
        `;
      }
    }
  }
  </script>
  
  <style scoped>
  </style>
  