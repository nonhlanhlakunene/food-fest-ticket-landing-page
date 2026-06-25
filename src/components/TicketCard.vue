<template>
  <div class="card" :class="{ featured: ticket.featured }">

    <div v-if="ticket.featured" class="featured-badge">⭐ Most Popular</div>

    <div class="card-header">
      <h2 class="tier-name">{{ ticket.tier }}</h2>
      <p class="tier-price">R {{ ticket.price }} <span>/ person</span></p>
    </div>

    <p class="tier-description">{{ ticket.description }}</p>

    <ul class="benefits-list">
      <li v-for="(benefit, index) in ticket.benefits" :key="index">
        ✅ {{ benefit }}
      </li>
    </ul>

    <div class="card-footer">
      <button class="notify-btn">Notify Me</button>
      <button class="fav-btn" @click="toggleFavourite">
        {{ isFavourited ? '❤️' : '🤍' }} {{ isFavourited ? 'Saved' : 'Save' }}
      </button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'TicketCard',

  props: {
    ticket: {
      type: Object,
      required: true
    },
    favouriteIds: {
      type: Array,
      required: true
    }
  },

  emits: ['toggle-favourite'],

  computed: {
    isFavourited: function () {
      return this.favouriteIds.includes(this.ticket.id)
    }
  },

  methods: {
    toggleFavourite: function () {
      this.$emit('toggle-favourite', this.ticket.id)
    }
  }
}
</script>