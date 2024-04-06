<script setup lang="ts">
import {
  Search,
  MoreHorizontal,
  ChevronsLeft,
  ChevronLeft,
  ChevronsRight,
  ChevronRight
} from 'lucide-vue-next'

defineProps<{ msg: string }>()

const lines = Array.from({ length: 5 })
</script>

<template>
  <div class="flex flex-col gap-4">
    <div class="flex gap-3 items-center">
      <h1 class="text-2xl font-bold">Participantes</h1>

      <div
        class="flex items-center gap-3 w-72 h-9 px-3 py-1.5 bg-transparent border border-white/10 rounded-lg"
      >
        <Search class="size-4 text-emerald-200" />
        <input
          placeholder="Buscar participante..."
          class="flex-1 bg-transparent outline-none border-none text-sm p-0"
        />
      </div>
    </div>

    <div class="border border-white/10 rounded-lg">
      <table class="w-full">
        <thead>
          <tr class="border-b border-white/10">
            <th width="48px">
              <input
                type="checkbox"
                name=""
                id=""
                class="size-4 bg-black/20 rounded border-white/10 cursor-pointer"
              />
            </th>
            <th class="py-3 px-4 text-sm font-semibold text-left">Código</th>
            <th class="py-3 px-4 text-sm font-semibold text-left">Participante</th>
            <th class="py-3 px-4 text-sm font-semibold text-left">Data de inscrição</th>
            <th class="py-3 px-4 text-sm font-semibold text-left">Data do check-in</th>
            <th width="64px"></th>
          </tr>
        </thead>

        <tbody>
          <tr
            v-for="(line, index) in lines"
            :key="index"
            class="border-b border-white/10 hover:bg-zinc-50/5 transition-colors"
          >
            <td class="py-3 px-4 text-sm text-zinc-300">
              <input
                type="checkbox"
                name=""
                id=""
                class="size-4 bg-black/20 rounded border-white/10 cursor-pointer"
              />
            </td>
            <td class="py-3 px-4 text-sm text-zinc-300">1234</td>
            <td class="py-3 px-4 text-sm text-zinc-300">
              <div class="flex flex-col gap-1">
                <span class="font-semibold text-white">Marlon Victor</span>
                <span>cmarlonvictor@gmail.com</span>
              </div>
            </td>
            <td class="py-3 px-4 text-sm text-zinc-300">7 dias atrás</td>
            <td class="py-3 px-4 text-sm text-zinc-300">3 dias atrás</td>
            <td class="py-3 px-4 text-sm text-zinc-300">
              <button class="bg-black/20 border border-white/10 rounded-md p-1.5">
                <MoreHorizontal class="size-4" />
              </button>
            </td>
          </tr>
        </tbody>

        <tfoot>
          <tr>
            <td colspan="3" class="py-3 px-4 text-sm text-zinc-300">Mostrando 5 de 228 itens</td>
            <td colspan="3" class="py-3 px-4 text-sm text-zinc-300 text-right">
              <div class="inline-flex items-center gap-8">
                <span>Página 1 de 23</span>

                <div class="flex gap-1.5">
                  <button class="bg-white/10 border border-white/10 rounded-md p-1.5">
                    <ChevronsLeft class="size-4" />
                  </button>
                  <button class="bg-white/10 border border-white/10 rounded-md p-1.5">
                    <ChevronLeft class="size-4" />
                  </button>
                  <button class="bg-white/10 border border-white/10 rounded-md p-1.5">
                    <ChevronRight class="size-4" />
                  </button>
                  <button class="bg-white/10 border border-white/10 rounded-md p-1.5">
                    <ChevronsRight class="size-4" />
                  </button>
                </div>
              </div>
            </td>
          </tr>
        </tfoot>
      </table>
    </div>
  </div>

  <!-- <h1 class="font-semibold text-3xl text-slate-300">{{ msg }}</h1> -->
</template>

<style scoped></style>
