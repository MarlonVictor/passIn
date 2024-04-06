<script setup lang="ts">
import {
  Search,
  MoreHorizontal,
  ChevronsLeft,
  ChevronLeft,
  ChevronsRight,
  ChevronRight
} from 'lucide-vue-next'

import IconButton from './IconButton.vue'
import Table from './table/Table.vue'
import TableHeader from './table/TableHeader.vue'
import TableCell from './table/TableCell.vue'

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

    <Table class="w-full">
      <thead>
        <tr class="border-b border-white/10">
          <TableHeader width="48px">
            <input
              type="checkbox"
              name=""
              id=""
              class="size-4 bg-black/20 rounded border-white/10 cursor-pointer"
            />
          </TableHeader>
          <TableHeader>Código</TableHeader>
          <TableHeader>Participante</TableHeader>
          <TableHeader>Data de inscrição</TableHeader>
          <TableHeader>Data do check-in</TableHeader>
          <TableHeader width="64px"></TableHeader>
        </tr>
      </thead>

      <tbody>
        <tr
          v-for="(_, index) in lines"
          :key="index"
          class="border-b border-white/10 hover:bg-zinc-50/5 transition-colors"
        >
          <TableCell>
            <input
              type="checkbox"
              name=""
              id=""
              class="size-4 bg-black/20 rounded border-white/10 cursor-pointer"
            />
          </TableCell>
          <TableCell>1234</TableCell>
          <TableCell>
            <div class="flex flex-col gap-1">
              <span class="font-semibold text-white">Marlon Victor</span>
              <span>cmarlonvictor@gmail.com</span>
            </div>
          </TableCell>
          <TableCell>7 dias atrás</TableCell>
          <TableCell>3 dias atrás</TableCell>
          <TableCell>
            <IconButton transparent>
              <MoreHorizontal class="size-4" />
            </IconButton>
          </TableCell>
        </tr>
      </tbody>

      <tfoot>
        <tr>
          <TableCell colspan="3">Mostrando 5 de 228 itens</TableCell>
          <TableCell colspan="3" class="text-right">
            <div class="inline-flex items-center gap-8">
              <span>Página 1 de 23</span>

              <div class="flex gap-1.5">
                <IconButton>
                  <ChevronsLeft class="size-4" />
                </IconButton>
                <IconButton>
                  <ChevronLeft class="size-4" />
                </IconButton>
                <IconButton>
                  <ChevronRight class="size-4" />
                </IconButton>
                <IconButton>
                  <ChevronsRight class="size-4" />
                </IconButton>
              </div>
            </div>
          </TableCell>
        </tr>
      </tfoot>
    </Table>
  </div>
</template>

<style scoped></style>
