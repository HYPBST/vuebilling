<template>
  <div>
      <table>
          <th>
              Név
          </th>
          <th>
              Ár
          </th>
          <th>
              Darabszám
          </th>
          <th>
              Operations
          </th>
          <RaktarItem
          v-for="row in rows"
          v-bind:key="row.title"
          :row="row"
          @raktar-item-changed="Changed"
          />
          <tr>
              <td>
                <input type="text" placeholder="Név">
              </td>
              <td>
                  <input type="number" placeholder="Ár">
              </td>
              <td>
                  <input type="number" placeholder="Darabszám">
              </td>
              <td>
                  <button> Hozzáad</button>
              </td>
          </tr>
      </table>
  </div>
</template>

<script>
import RaktarItem from './RaktarItem.vue'
export default {
    props: ['rows'],
    components: {RaktarItem},
    methods: {
        Changed(e) {
            this.$emit('raktar-item-changed', e)
        }
    }

}
</script>

