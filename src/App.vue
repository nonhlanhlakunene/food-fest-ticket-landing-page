<template>
  <div id="app">

    <header class="main-header">
      <h1>🍽️ Cape Town Food Fest 2026</h1>
      <p>A weekend of food, flavour & community. Choose your ticket below.</p>
    </header>

    <main class="container">

      <section class="tickets-grid">
        <TicketCard
          v-for="ticket in tickets"
          :key="ticket.id"
          :ticket="ticket"
          :favouriteIds="favouriteIds"
          @toggle-favourite="handleFavourite"
        />
      </section>

    </main>

  </div>
</template>

<script>
import TicketCard from './components/TicketCard.vue'
import tickets from './tickets.js'

export default {
  name: 'App',

  components: {
    TicketCard
  },

  data: function () {
    return {
      tickets: tickets,
      favouriteIds: []
    }
  },

  methods: {
    handleFavourite: function (id) {
      var index = this.favouriteIds.indexOf(id)
      if (index === -1) {
        this.favouriteIds.push(id)
      } else {
        this.favouriteIds.splice(index, 1)
      }
    }
  }
}
</script>