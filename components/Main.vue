<template> 
  <div v-if="open">
    <button  type="button" class="rounded bg-indigo-600 px-2 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline 
     focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="msg()">Data</button>
   
     <section aria-labelledby="notes-title">
      
      <div
      
      class="bg-white shadow sm:overflow-hidden sm:rounded-lg"
      
      >
      
      <div class="divide-y divide-gray-200">
      
      <div class="px-4 py-5 sm:px-6"></div>
      
      <div class="px-4 py-6 sm:px-6">
      
      <ul role="list" class="space-y-8">
      
      <li v-for="name in cdata1" :key="name.id">
      
      <div class="flex space-x-3">
      
      <div>
      
      <div class="text-sm flex flex-row">
        <div class="flex-shrink-0">
            <img class="h-10 w-10 rounded-full" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" />
          </div>
      <a
      
      href="#"
      
      class="font-medium text-gray-900"
      
      @mouseover="showhover = true"
      
      @mouseout="showhover = false"
      
      >mounika meesa</a>
      
      <PencilSquareIcon
      
      name="iconoir:edit-pencil"
      
      size="20"
      
      class="h-5 w-5 flex-shrink-0 text-gray-400 group-hover:text-gray-500"
      
      @click="editNote(name)">
      
      <Edit :model="model" :name="name.cdata1"></Edit>
      
      </PencilSquareIcon>
      
      <TrashIcon
      
      name="bytesize:trash"
      
      size="16"
      
      class="h-5 w-5 flex-shrink-0 text-gray-400 group-hover:text-gray-500:text-red-600"
      
      @click="deleteNote(name)">
      
      </TrashIcon>
      <!-- <PencilSquareIcon
      name="iconoir:edit-pencil"
      size="20"
      class="h-5 w-5 flex-shrink-0 text-gray-400 group-hover:text-gray-500" @click="message=!message" >
      </PencilSquareIcon> -->
      <div @click="message=!message">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6" >
  <path stroke-linecap="round" stroke-linejoin="round" d="M15 11.25l-3-3m0 0l-3 3m3-3v7.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
</svg></div>

      <div class="border-b border-gray-200 bg-white px-4 py-5 sm:px-6">
    
    </div>
      </div>
      
      <div class="mt-1 text-sm text-gray-700">
      
      <p>{{ name.cdata1 }}</p>
      
      </div>
      
      <div class="mt-2 space-x-2 text-sm">
      
      <span
      
      class="font-medium text-gray-500"
      
      >{{name.date }}</span
      
      >
      <Activity v-if="!message" :name="name.cdata1" :id="name.id"></Activity>
      </div>
      
      </div>
      
      </div>
      
      </li>
      
      </ul>
      
      </div>
      
      </div>
      
      </div>
      
      </section>
    </div>
     <TransitionRoot as="template" :show="!open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100" leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
          <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
        </TransitionChild>
  
        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
            <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95" enter-to="opacity-100 translate-y-0 sm:scale-100" leave="ease-in duration-200" leave-from="opacity-100 translate-y-0 sm:scale-100" leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95">
              <DialogPanel class="relative transform overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6">
                <div>
                  
                  <div class="mt-3 text-center sm:mt-5">
                    <DialogTitle as="h3" class="text-base font-semibold leading-6 text-gray-900">Data</DialogTitle>
                    <div>
       <div class="mt-2">
        
         <input type="text" v-model="data1" name="name" id="name" class="block w-full rounded-full border-0 px-4 py-1.5 text-gray-900 shadow-sm ring-1 
         ring-inset ring-gray-300 
         placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"  /> 
   </div>
   </div>
                  </div>
                </div>
                <div class="mt-5 sm:mt-6 sm:grid sm:grid-flow-row-dense sm:grid-cols-2 sm:gap-3 justify-between align item-center">
                
                  <button type="button" class="inline-flex w-full justify-center rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 sm:col-start-2"  @click="postData">Add</button>
                  <button type="button" class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:col-start-1 sm:mt-0" @click="open = true" ref="cancelButtonRef">Cancel</button>
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  
          <!-- <Add v-if="!message" :message="message" @add-template="postData"></Add> -->
         <List></List>
         <div class="row-span-3 col-span-4 bg-white h-[calc(100vh-150px)]">
         <CollectionAdd v-if="type == 'add'"  />
         <CollectionEdit
           v-else
           :template="template"
           @edit-template="editTemplate"
           :key="render"
         />
       </div>
   </template>
   <script setup>
   import { ref } from "vue";
   import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot } from '@headlessui/vue'
  import { CheckIcon } from '@heroicons/vue/24/outline'
   import {
   XMarkIcon,
   PencilSquareIcon,
   TrashIcon,
   ActivityIcon
   } from "@heroicons/vue/24/outline";
   
   const activity=ref([])
     const  action=ref()
     
      const cdata2=ref()
       const cdata3=ref()
       const message=ref([false])
       let data1 = ref("");
       const msg = () => {
          open.value=!open.value
     };
   const props = defineProps({
     // Get Template Mail Data
     url: { type: String, default: "" },
     addUrl: { type: String, default: "" },
   });
   const template = ref({
     name: "Edit",
     subject: "Editsubject",
     body: "Editbody",
   });
   async function postData() {
    open.value = true
     const postoptions = {
       method: "POST",
       headers: {
         "Content-Type": "application/json",
         Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYmZlOTY3MDc0YzJhNGVlNDhiODFlYWU1ZmU5ZThhMjkiLCJkIjoiMTY4MDA4MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzkyNzB9._HklK6rl9AWu3mp4kRdrOIsxyEP-jNpG7kgF3K-5GlA`,
       },
       body: {
         project_id: "1",
       entity_id: "1415",
       entity: "CONTACTS",
       activity: [],
       cdata1: data1.value,
       // cdata2:  data.cdata2,
       // cdata3: data.cdata3,
       },
     };
     const data = await useAuthLazyFetch(
       "https://v1-orm-lib.mars.hipso.cc/activities/",
       postoptions
     );
     cdata1.value.push({
       project_id: "1",
       entity_id: "1415",
       entity: "CONTACTS",
       activity: [],
      //  action: action.value,
       cdata1: data1.value,
       // cdata2:  cdata2.value,
       // cdata3: cdata3.value,
     });
     data1.value = ''
   }
   const { pending, data: cdata1 } = await useAuthLazyFetch(
      
      "https://v1-orm-lib.mars.hipso.cc/activities/CONTACTS/1415?offset=0&limit=100&sort_column=id&sort_direction=desc",
      
      {}
      
      );
   const open = ref(true);
      function opensidebar() {
      open.value = !open.value;}
    
   </script>