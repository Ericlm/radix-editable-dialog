<script setup lang="ts">
import { Dialog, Editable } from 'radix-vue/namespaced';
import { ref } from 'vue';

const open = ref(false);
</script>

<template>
  <Dialog.Root v-model:open="open">
    <Dialog.Trigger>
      Trigger
    </Dialog.Trigger>

    <Dialog.Portal>
      <Dialog.Overlay class="fixed inset-0 bg-gray-500/75" />

      <div v-if="open" class="fixed inset-0 w-screen overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
          <Dialog.Content as="form"
            class="relative overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6">
            <div>
              <div class="mx-auto flex size-12 items-center justify-center rounded-full bg-blue-100">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                  class="size-6 text-blue-600" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                  stroke-linejoin="round">
                  <path d="M4 19.5v-15A2.5 2.5 0 0 1 6.5 2H19a1 1 0 0 1 1 1v18a1 1 0 0 1-1 1H6.5a1 1 0 0 1 0-5H20" />
                </svg>
              </div>

              <div class="mt-3 text-center sm:mt-5">
                <Dialog.Title class="text-base font-semibold leading-6 text-gray-900">
                  Dialog Title
                </Dialog.Title>

                <div class="mt-2">
                  <Dialog.Description class="text-sm text-gray-500">
                    Dialog description, Lorem, ipsum dolor sit amet consectetur adipisicing elit. Excepturi, inventore.
                  </Dialog.Description>
                </div>
              </div>

              <div>
                <Editable.Root v-slot="{ isEditing }">
                  <Editable.Area :class="[isEditing ? 'bg-blue-50' : 'bg-white']">
                    <Editable.Preview />
                    <Editable.Input />
                  </Editable.Area>

                  <Editable.SubmitTrigger>
                    Submit
                  </Editable.SubmitTrigger>
                </Editable.Root>
              </div>
            </div>

            <div class="mt-5 sm:mt-6 sm:grid sm:grid-flow-row-dense sm:grid-cols-2 sm:gap-3">
              <button
                class="inline-flex w-full justify-center rounded-md bg-blue-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-blue-500 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 sm:col-start-2"
                type="button" @click="open = false">
                Submit
              </button>

              <Dialog.Close
                class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:col-start-1 sm:mt-0">
                Cancel
              </Dialog.Close>
            </div>
          </Dialog.Content>
        </div>
      </div>
    </Dialog.Portal>
  </Dialog.Root>

  <Editable.Root v-slot="{ isEditing }">
    <Editable.Area :class="[isEditing ? 'bg-blue-50' : 'bg-white']">
      <Editable.Preview />
      <Editable.Input />
    </Editable.Area>

    <Editable.SubmitTrigger>
      Submit
    </Editable.SubmitTrigger>
  </Editable.Root>
</template>
