<script setup>
import RenderModal from '../AsyncComponent/RenderModal.vue';
import SavetoLocal from '../ComposableTest/SavetoLocal.vue';
import CustomeDirectives from '../CustomDirectives/CustomeDirectives.vue';
import { ref } from 'vue';

const currentTab = ref('RenderModal')

const tabs ={
  RenderModal,
  SavetoLocal,
  CustomeDirectives
}

</script>

<template>
<div class="drawer lg:drawer-open">
  <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
  <div class="drawer-content flex flex-col items-center justify-center">
    <!-- Page content here -->
    <component :is="tabs[currentTab]"></component>
  </div>
  <div class="drawer-side">
    <label for="my-drawer-2" aria-label="close sidebar" class="drawer-overlay"></label>
    <ul class="menu bg-base-200 text-base-content min-h-full w-80 p-4">
      <!-- Sidebar content here -->
      <li v-for="(_, tabIndex) in tabs" :key="tabIndex" >
        <button @click="currentTab = tabIndex" :class="{active: currentTab === tabIndex}">
          {{ tabIndex }}
        </button>
      </li>
    </ul>
  </div>
</div>
</template>