<template>
  <div>
    <div>
      <!--      <a @click="changeLocale('en')" href="#">English</a> / <a @click="changeLocale('pt_BR')" href="#">Português</a>-->
    </div>

    <div class="header">
      <span v-on:click="scrollTo('Manovale')" style="color: orange">Manovale</span> |
      <span v-on:click="scrollTo('Artigiano')" style="color: brown">Artigiano</span> |
      <span v-on:click="scrollTo('Architetto')" style="color: gray">Architetto</span> |
      <span v-on:click="scrollTo('Legionario')" style="color: red">Legionario</span> |
      <span v-on:click="scrollTo('Mercante')" style="color: blue">Mercante</span> |
      <span v-on:click="scrollTo('Patrono')" style="color: purple">Patrono</span>
    </div>

    <section v-for="card in filteredItems" :key="card.name">
      <h1 :id="card.name" :style=getCardColor(card)>{{ card.name }}</h1>
      <p style="text-align: left">{{ $t('card ' + card.name) }}</p>
    </section>

  </div>
</template>

<script>
window.addEventListener('beforeunload', function (e) {
  e.preventDefault();
  e.returnValue = '';
});

let cards = [
  {name: "Casa Popolare", role: "Manovale"},
  {name: "Latrina", role: "Manovale"},
  {name: "Strada", role: "Manovale"},
  {name: "Osteria", role: "Manovale"},

  {name: "Mercato", role: "Artigiano"},
  {name: "Palizzata", role: "Artigiano"},
  {name: "Porto", role: "Artigiano"},
  {name: "Circo", role: "Artigiano"},

  {name: "Accademia", role: "Legionario"},
  {name: "Arco", role: "Legionario"},
  {name: "Atrio", role: "Legionario"},
  {name: "Porta", role: "Legionario"},
  {name: "Forgia", role: "Legionario"},
  {name: "Santuario", role: "Legionario"},
  {name: "Scuola", role: "Legionario"},
  {name: "Terme", role: "Legionario"},

  {name: "Vomitorium", role: "Architetto"},
  {name: "Torre", role: "Architetto"},
  {name: "Muro", role: "Architetto"},
  {name: "Dispensa", role: "Architetto"},
  {name: "Anfiteatro", role: "Architetto"},
  {name: "Acquedotto", role: "Architetto"},
  {name: "Senato", role: "Architetto"},
  {name: "Ponte", role: "Architetto"},

  {name: "Catacombe", role: "Mercante"},
  {name: "Circo Massimo", role: "Mercante"},
  {name: "Colosseo", role: "Mercante"},
  {name: "Fogna", role: "Mercante"},
  {name: "Giardino", role: "Mercante"},
  {name: "Prigione", role: "Mercante"},
  {name: "Studio", role: "Mercante"},
  {name: "Villa", role: "Mercante"},

  {name: "Foro", role: "Patrono"},
  {name: "Tempio", role: "Patrono"},
  {name: "Basilica", role: "Patrono"},
  {name: "Fontana", role: "Patrono"},
  {name: "Statua", role: "Patrono"},
  {name: "Scalinata", role: "Patrono"},
  {name: "Palazzo", role: "Patrono"},
  {name: "Ludus Magnus", role: "Patrono"},
]


export default {
  name: 'Application',
  methods: {
    scrollTo(role) {
      let card = cards.find((card) => card.role === role)
      document.getElementById(card.name).scrollIntoView()
    },
    getCardColor(card) {
      var color;
      if (card.role === 'Manovale')
        color = 'orange'
      else if (card.role === 'Artigiano')
        color = 'brown'
      else if (card.role === 'Legionario')
        color = 'red'
      else if (card.role === 'Architetto')
        color = 'grey'
      else if (card.role === 'Mercante')
        color = 'blue'
      else
        color = 'purple'

      return 'scroll-margin: 20px; text-align: left; color: ' + color
    },
  },
  computed: {
    filteredItems() {
      return this.cards.filter(card => {
        return card.name.toUpperCase().startsWith(this.search.toUpperCase())
      })
    }
  },

  data() {
    return {
      search: '',
      cards
    }
  }
}
</script>

<style scoped>
.header {
  user-select: none;

  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;

  font-size: 20px;
  text-align: left;
  font-weight: bold;
  border-top: 1px solid;
  background-color: white;
  padding: 10px;
}

.header span {
  cursor: pointer;
}
</style>
