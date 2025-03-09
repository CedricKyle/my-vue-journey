<script setup>
import RenderModal from '../AsyncComponent/RenderModal.vue';
import SavetoLocal from '../ComposableTest/SavetoLocal.vue';
import CustomeDirectives from '../CustomDirectives/CustomeDirectives.vue';
import Whatis from './Whatis.vue';
import HowItWork from './HowItWork.vue';
import WhyUseFull from './WhyUseFull.vue';
import { Home, FileText, Settings } from 'lucide-vue-next'; // Import icons
import { ref } from 'vue';

const currentTab = ref('RenderModal')
const basicCurrentTab = ref(null)

const tabs ={
  RenderModal: { component: RenderModal, icon: Home }, 
  SavetoLocal: { component: SavetoLocal, icon: FileText }, 
  CustomeDirectives: { component: CustomeDirectives, icon: Settings }
}

const basicTabs = {
  //This is sample basic dynamic component
  Whatis,
  HowItWork,
  WhyUseFull
}

// Function para i-reset ang basicCurrentTab kapag may pinili sa main tabs
const selectMainTab = (tab) => {
  currentTab.value = tab;
  basicCurrentTab.value = null; // Hide basic tab kapag nagpalit ng main tab
};

// Function para i-reset ang currentTab kapag may pinili sa basic tabs
const selectBasicTab = (tab) => {
  basicCurrentTab.value = tab;
  currentTab.value = null; // Hide main tab kapag nagpalit ng basic tab
};

</script>

<template>
<div class="drawer lg:drawer-open">
  <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
  <div class="drawer-content flex flex-col items-center justify-center">
    <!-- Page content here -->
    <component v-if="currentTab" :is="tabs[currentTab].component"></component>
    <component v-if="basicCurrentTab" :is="basicTabs[basicCurrentTab]"></component>
  </div>
  <div class="drawer-side">
    <label for="my-drawer-2" aria-label="close sidebar" class="drawer-overlay"></label>
    <ul class="menu bg-base-200 text-base-content min-h-full w-80 p-4">
      <!-- Sidebar content here -->
      <li v-for="(tab, tabIndex) in tabs" :key="tabIndex" class="m-2">
        <button @click="selectMainTab(tabIndex)" :class="{active: currentTab === tabIndex}">
          <component :is="tab.icon" class="w-5 h-5" />
          {{ tabIndex }}
        </button>
      </li>

      <div class=" flex flex-col gap-3 pt-110 m-2">
        <a @click="selectBasicTab('Whatis')" class="cursor-pointer hover:underline">What is Dynamic Component</a>
        <a @click="selectBasicTab('HowItWork')" class="cursor-pointer hover:underline">How it Works</a>
        <a @click="selectBasicTab('WhyUseFull')" class="cursor-pointer hover:underline">Why is it Usefull</a>
      </div>
    </ul>
  </div>
</div>
</template>