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
                <input type="text" v-model="title" placeholder="Név">
              </td>
              <td>
                  <input type="number" v-model="price" placeholder="Ár">
              </td>
              <td>
                  <input type="number" v-model="quantity" placeholder="Darabszám">
              </td>
              <td>
                  <button @click="Post"> Hozzáad</button>
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
        },
        Post(){
            this.$emit('raktar-item-post', {
                new:{
                    title:this.title,
                    price:this.price,
                    quantity:this.quantity
                }
            })
            this.title="",
            this.price=null,
            this.quantity=null
        }
    }

}
</script>

