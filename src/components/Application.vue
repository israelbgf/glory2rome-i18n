<template>
  <div>
    <div>
      <!--      <a @click="changeLocale('en')" href="#">English</a> / <a @click="changeLocale('pt_BR')" href="#">Português</a>-->
    </div>

    <div style="font-size: 20px; text-align: left; font-weight: bold">
      <span style="color: orange">Manovale</span> |
      <span style="color: brown">Artigiano</span> |
      <span style="color: gray">Architetto</span> |
      <span style="color: red">Legionario</span> |
      <span style="color: blue">Mercante</span> |
      <span style="color: purple">Patrono</span>
    </div>

    <div style="border: 1px dashed gray; margin-top: 5px; margin-bottom: 5px"/>

    <section v-for="card in filteredItems" :key="card">
      <h1 :style=getCardColor(card)>{{ card.name }}</h1>
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
  {name: "Casa Popolare", type: "Manovale"},
  {name: "Latrina", type: "Manovale"},
  {name: "Strada", type: "Manovale"},
  {name: "Osteria", type: "Manovale"},

  {name: "Mercato", type: "Artigiano"},
  {name: "Palizzata", type: "Artigiano"},
  {name: "Porto", type: "Artigiano"},
  {name: "Circo", type: "Artigiano"},

  {name: "Accademia", type: "Legionario"},
  {name: "Arco", type: "Legionario"},
  {name: "Atrio", type: "Legionario"},
  {name: "Porta", type: "Legionario"},
  {name: "Forgia", type: "Legionario"},
  {name: "Santuario", type: "Legionario"},
  {name: "Scuola", type: "Legionario"},
  {name: "Terme", type: "Legionario"},

  {name: "Vomitorium", type: "Architetto"},
  {name: "Torre", type: "Architetto"},
  {name: "Muro", type: "Architetto"},
  {name: "Dispensa", type: "Architetto"},
  {name: "Anfiteatro", type: "Architetto"},
  {name: "Acquedotto", type: "Architetto"},
  {name: "Senato", type: "Architetto"},
  {name: "Ponte", type: "Architetto"},

  {name: "Catacombe", type: "Mercante"},
  {name: "Circo Massimo", type: "Mercante"},
  {name: "Colosseo", type: "Mercante"},
  {name: "Fogna", type: "Mercante"},
  {name: "Giardino", type: "Mercante"},
  {name: "Prigione", type: "Mercante"},
  {name: "Studio", type: "Mercante"},
  {name: "Villa", type: "Mercante"},

  {name: "Foro", type: "Patrono"},
  {name: "Tempio", type: "Patrono"},
  {name: "Basilica", type: "Patrono"},
  {name: "Fontana", type: "Patrono"},
  {name: "Statua", type: "Patrono"},
  {name: "Scalinata", type: "Patrono"},
  {name: "Palazzo", type: "Patrono"},
  {name: "Ludus Magnus", type: "Patrono"},
]


export default {
  name: 'Application',
  methods: {
    getCardColor(card) {
      var color;
      if (card.type === 'Manovale')
        color = 'orange'
      else if (card.type === 'Artigiano')
        color = 'brown'
      else if (card.type === 'Legionario')
        color = 'red'
      else if (card.type === 'Architetto')
        color = 'grey'
      else if (card.type === 'Mercante')
        color = 'blue'
      else
        color = 'purple'

      return 'text-align: left; color: ' + color
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

</style>
