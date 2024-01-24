<script setup lang="ts">
import { onMounted } from 'vue';


interface CardDetails {
  title: string;
  estimative: number;
}

interface Card {
  name: string;
  cards: CardDetails[];
}

interface Board {
  name: string;
  columns: Card[];
}

const board: Board = {
  name: "HelloWorld",
  columns: [
    {
      name: "Todo",
      cards: [
        {
          title: "A",
          estimative: 3
        },
        {
          title: "B",
          estimative: 2
        },
        {
          title: "C",
          estimative: 1
        }
      ]
    },
    {
      name: "Doing",
      cards: []
    },
    {
      name: "Done",
      cards: []
    }
  ]
};

onMounted(()=> {
  console.log("montou");
});
</script>

<template>
  <h1>{{ board.name }}</h1>
  <div class="columns">
    <div
      class="column"
      v-for="column in board.columns" 
      :key="column.name"
    >
      {{ column.name }}
      <div 
        class="card-title"
        v-for="card in column.cards"
      >
        {{ card.title }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.columns {
  display: flex;
  flex-direction: row;
}

.column {
  width: 200px;
}
</style>
