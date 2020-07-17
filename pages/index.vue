<template>
  <section class="section">
    <div class="columns is-mobile">
      <div id="app" class="container">

        <section>
          <p class="content"><b>Selected:</b> {{ selected }}</p>
          <b-field label="Find a JS framework">
            <b-autocomplete
              rounded
              v-model="name"
              :data="filteredDataArray"
              placeholder="e.g. jQuery"
              icon="magnify"
              clearable
              @select="option => selected = option">
              <template slot="empty">No results found</template>
            </b-autocomplete>
          </b-field>
        </section>

      </div>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'

const example = {
  data() {
    return {
      data: [
        'Angular',
        'Angular 2',
        'Aurelia',
        'Backbone',
        'Ember',
        'jQuery',
        'Meteor',
        'Node.js',
        'Polymer',
        'React',
        'RxJS',
        'Vue.js'
      ],
      name: '',
      selected: null
    }
  },
  computed: {
    filteredDataArray() {
      return this.data.filter((option) => {
        return option
          .toString()
          .toLowerCase()
          .indexOf(this.name.toLowerCase()) >= 0
      })
    }
  }
}


export default {
  name: 'HomePage',

  components: {
    Card
  }

}
</script>

<style>

</style>
