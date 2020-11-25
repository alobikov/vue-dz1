<template>
  <div v-show="isInputActive" class="container">
    <div class="row">
      <label for="email">Email</label>
      <input name="email " type="text" v-model="host.email" />
    </div>
    <div class="row">
      <label for="first">First Name</label>
      <input name="first" type="text" v-model="host.first" />
    </div>
    <div class="row">
      <label for="last">Last Name</label>
      <input name="last" type="text" v-model="host.last" />
    </div>
    <div class="row">
      <label for="phone">First Name</label>
      <input name="phone" type="text" v-model="host.phone" />
    </div>
    <div class="row horizontal">
      <p>Guests</p>
      &nbsp;
      <button @click="addGuest">+</button>
    </div>
    <div v-for="(guest, idx) in guests" class="row" :key="idx">
      <label @click="removeGuest(idx)" :for="guest + idx">Guest{{ idx }}</label>
      <input
        :name="guest + idx"
        type="text"
        :value="guest"
        @input="recordGuest($event, idx)"
      />
    </div>

    <div class="row">
      <button @click="onSubmit" :style="{ margin: 0, height: '30px' }">
        Submit
      </button>
    </div>
    <div>
      <h1>test</h1>
      <table>
        <tr>
          <td>td</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data: function () {
    return {
      isInputActive: false,
      host: {
        first: 'Name',
        last: '',
        phone: '',
        email: ''
      },
      guests: []
    }
  },
  computed: {
    fullName: function () {
      return this.host.first + ' ' + this.host.last
    }
  },
  methods: {
    addGuest() {
      this.guests.push('')
    },
    recordGuest($event, idx) {
      this.guests[idx] = $event.target.value
    },
    removeGuest(idx) {
      console.log('remove')
      this.guests.splice(idx, 1)
    },
    onSubmit() {}
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 24px;
}
.row {
  display: flex;
  flex-direction: column;
  width: 50%;
  justify-content: flex-start;
  align-items: flex-start;
  background-color: rgb(221, 226, 226);
  padding: 8px 0 8px 20px;
}
.horizontal {
  flex-direction: row;
  align-items: center;
}
button {
  margin-left: 12px;
}
table {
  width: 100%;
}
</style>
