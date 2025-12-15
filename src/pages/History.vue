<template>
  <AppHeader />
  <div class="min-h-screen bg-white px-6 py-10">

    <h1 class="text-4xl font-bold text-center mb-12">History</h1>
    <img src="/molekul_kiriR.png" class="absolute top-0 left-0 w-[300px] h-[400px] opacity-50">

    <div class="space-y-10 max-w-5xl mx-auto">
      <!-- Loop history items -->
      <div 
        v-for="item in history" 
        :key="item.id" 
        class="w-full border-b pb-6 flex justify-between items-start relative"
      >
        <div class="text-gray-700 space-y-1">
          <p><span class="font-semibold">SMILES:</span> {{ item.smiles ?? "N/A" }}</p>
          <p><span class="font-semibold">pIC50:</span> {{ item.pLC50 ?? "N/A" }}</p>
          <p><span class="font-semibold">Atom Count:</span> {{ item.atom_count ?? "N/A" }}</p>
          <p><span class="font-semibold">LogP:</span> {{ item.logP ?? "N/A" }}</p>
          <p><span class="font-semibold">Justification:</span> {{ item.justification ?? "No justification" }}</p>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import AppHeader from '../components/AppHeader.vue'

const history = ref([])

onMounted(async () => {
  const userId = localStorage.getItem("user_id")
  console.log("USER ID:", userId)

  if (!userId) {
    console.warn("User belum login, history tidak dimuat")
    return
  }

  try {
   const API_URL = import.meta.env.VITE_BACKEND_URL;
    const response = await axios.get(`${API_URL}/history/user/${userId}`)
    console.log("HISTORY RESPONSE:", response.data)

    // Pastikan semua field ada, jika null beri default
    history.value = response.data.history.map(h => ({
      id: h.id,
      user_id: h.user_id,
      smiles: h.smiles ?? "N/A",
      pLC50: h.pLC50 ?? "N/A",
      atom_count: h.atom_count ?? "N/A",
      logP: h.logP ?? "N/A",
      justification: h.justification ?? "No justification"
    }))
    
  } catch (err) {
    console.error("Failed to fetch history:", err)
  }
})
</script>
