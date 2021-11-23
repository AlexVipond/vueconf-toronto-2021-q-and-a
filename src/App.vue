<template>
  <!-- Input is just a focus target for testing tab navigation -->
  <input type="text" />
  <div class="flex flex-col gap-8 p-8 pb-10">
    <div :ref="listbox.root.ref" class="max-w-md border border-gray-600 rounded">
      <div
        v-for="(option, index) in optionsRef"
        :key="optionsRef[index]"
        :ref="listbox.options.getRef(index)"
        class="flex items-center gap-2 p-2"
      >
        <span>{{ option }}</span>
        <div class="ml-auto flex gap-2">
          <div class="relative text-xs uppercase tracking-widest">
            <span
              class="absolute inset-0 py-2px px-1 rounded bg-green-700 text-green-200"
              v-show="listbox.is.selected(index)">
              selected
            </span>
            <span class="py-2px px-1 opacity-0">selected</span>
          </div>
          <div class="relative text-xs uppercase tracking-widest">
            <span
              class="absolute inset-0 py-2px px-1 rounded bg-blue-700 text-blue-200"
              v-show="listbox.is.active(index)">
              active
            </span>
            <span class="py-2px px-1 opacity-0">active</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useListbox } from '@baleada/vue-features'
import { createReplace } from '@baleada/logic'
import { names as options } from '@alexvipond/mulago-foundation-portfolio'

const optionsRef = ref(options)

const listbox = useListbox({
  orientation: 'vertical',
});
</script>
