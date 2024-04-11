<script setup lang="ts">
import { formatDistanceToNow } from 'date-fns'
import { ptBR } from 'date-fns/locale'
import { computed, ref, watch } from 'vue'

import {
  ChevronLeft,
  ChevronRight,
  ChevronsLeft,
  ChevronsRight,
  MoreHorizontal,
  Search
} from 'lucide-vue-next'

// import { attendees } from '@/data/attendees'

import IconButton from './IconButton.vue'
import Table from './table/Table.vue'
import TableCell from './table/TableCell.vue'
import TableHeader from './table/TableHeader.vue'

interface Attendee {
  id: string
  name: string
  email: string
  createdAt: string
  checkedInAt: string | null
}

const dateConfig = { locale: ptBR, addSuffix: true }

// page configuration
const page = ref<number>(1)
const total = ref<number>(0)
const totalPages = computed(() => Math.ceil(total.value / 10))

const goToNextPage = () => (page.value += 1)
const goToPreviousPage = () => (page.value -= 1)
const goToFirstPage = () => (page.value = 1)
const goToLastPage = () => (page.value = totalPages.value)

// fetching data
const search = ref<string>('')
const attendees = ref<Attendee[]>([])

watch(
  () => [page.value, search.value],
  () => {
    const url = new URL(
      'http://localhost:3333/events/9e9bd979-9d10-4915-b339-3786b1634f33/attendees'
    )

    url.searchParams.set('pageIndex', String(page.value - 1))

    if (search.value.length > 0) {
      url.searchParams.set('query', search.value)
      page.value = 1
    }

    fetch(url)
      .then((res) => res.json())
      .then((data) => {
        attendees.value = data.attendees
        total.value = data.total
      })
  },
  { immediate: true }
)
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
          v-model="search"
          placeholder="Buscar participante..."
          class="flex-1 bg-transparent outline-none border-none text-sm p-0 focus:ring-0"
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
          v-for="attendee in attendees"
          :key="attendee.id"
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
          <TableCell>{{ attendee?.id }}</TableCell>
          <TableCell>
            <div class="flex flex-col gap-1">
              <span class="font-semibold text-white">{{ attendee?.name }}</span>
              <span>{{ attendee?.email }}</span>
            </div>
          </TableCell>
          <TableCell>
            {{ formatDistanceToNow(attendee.createdAt, dateConfig) }}
          </TableCell>
          <TableCell>
            {{
              attendee.checkedInAt
                ? formatDistanceToNow(attendee.checkedInAt, dateConfig)
                : 'Não fez check-in'
            }}
          </TableCell>
          <TableCell>
            <IconButton transparent>
              <MoreHorizontal class="size-4" />
            </IconButton>
          </TableCell>
        </tr>
      </tbody>

      <tfoot>
        <tr>
          <TableCell colspan="3">Mostrando {{ attendees.length }} de {{ total }} itens</TableCell>
          <TableCell colspan="3" class="text-right">
            <div class="inline-flex items-center gap-8">
              <span>Página {{ page }} de {{ totalPages }}</span>

              <div class="flex gap-1.5">
                <IconButton :disabled="page === 1" @click="goToFirstPage">
                  <ChevronsLeft class="size-4" />
                </IconButton>
                <IconButton :disabled="page === 1" @click="goToPreviousPage">
                  <ChevronLeft class="size-4" />
                </IconButton>
                <IconButton :disabled="page === totalPages" @click="goToNextPage">
                  <ChevronRight class="size-4" />
                </IconButton>
                <IconButton :disabled="page === totalPages" @click="goToLastPage">
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
