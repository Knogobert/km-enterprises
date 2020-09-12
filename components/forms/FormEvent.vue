<template>
  <form
    class="form my-8"
    name="event"
    action="/thanks"
    method="post"
    data-netlify="true"
    data-netlify-honeypot="honung"
  >
    <input type="hidden" name="form-name" value="event" />
    <div class="flex flex-wrap">
      <h4 class="subsubtitle mb-0 text-center w-full">Kontaktinformation</h4>
      <p class="form-control w-full sm:w-1/2">
        <label>Emailadress</label>
        <input
          v-model="event.email"
          type="email"
          name="email"
          required
          :class="{ filled: event.email }"
          placeholder="kungen@sverige.se"
        />
      </p>
      <p class="form-control w-full sm:w-1/2">
        <label>Telefonnummer</label>
        <input
          v-model="event.tel"
          type="tel"
          name="tel"
          required
          :class="{ filled: event.tel }"
          placeholder="+46 701 555 555"
        />
      </p>
    </div>

    <div>
      <h4 class="subsubtitle mt-8 text-center">Event</h4>
      <p class="form-control">
        <label>Plats</label>
        <input
          v-model="event.place"
          type="text"
          name="place"
          required
          :class="{ filled: event.place }"
          placeholder="Kungsgatan 11, 55500 Stockholm"
        />
      </p>
      <div class="flex flex-wrap">
        <p class="form-control w-full sm:w-1/2">
          <label>Datum</label>
          <input
            v-model="event.date"
            type="date"
            name="date"
            required
            :class="{ filled: event.date }"
          />
        </p>
        <p class="form-control w-full sm:w-1/2">
          <label>Tid</label>
          <input
            v-model="event.time"
            type="time"
            name="time"
            list="time-datalist"
            step="900"
            required
            :class="{ filled: event.time }"
          />
          <datalist id="time-datalist">
            <option value="7:00">7:00</option>
            <option value="8:00">8:00</option>
          </datalist>
        </p>
      </div>
      <p class="form-control hidden">
        <label>🍯Fyll inte i denna om du är en människa</label>
        <input name="honung" type="number" />
      </p>
      <p class="form-control">
        <label>Storlek på eventet</label>
        <input
          v-model="event.size"
          type="text"
          name="size"
          required
          :class="{ filled: event.size }"
          placeholder="Omkring 200 bjudna"
        />
      </p>
      <div class="form-control">
        <label class="pb-0">Uppskattad personalstyrka</label>
        <ul class="form-control">
          <li class="flex flex-wrap">
            <label for="waiter" class="w-full sm:w-1/2">Servitörer</label>
            <input
              v-model="event.staff.waiter"
              type="number"
              name="waiter"
              id="waiter"
              min="0"
              max="50"
              class="w-full sm:w-1/2"
            />
          </li>
          <li class="">
            <label for="bartender" class="w-full sm:w-1/2">Bartenders</label>
            <input
              v-model="event.staff.bartender"
              type="number"
              name="bartender"
              id="bartender"
              min="0"
              max="50"
              class="w-full sm:w-1/2"
            />
          </li>
          <li class="">
            <label for="dj" class="w-full sm:w-1/2">DJs</label>
            <input
              v-model="event.staff.dj"
              type="number"
              name="dj"
              id="dj"
              min="0"
              max="10"
              class="w-full sm:w-1/2"
            />
          </li>
        </ul>
      </div>
      <div class="form-control">
        <label class="pb-0">Tillägg</label>
        <p class="form-control form-control-radio">
          <label for="buy-alcohol"
            ><input
              v-model="event.extras"
              type="checkbox"
              name="buy-alcohol"
              id="buy-alcohol"
              class="btn"
              value="buy-alcohol"
            />
            Vi sköter alkoholinköpet - 1000kr</label
          >
          <label for="leave-alcohol"
            ><input
              v-model="event.extras"
              type="checkbox"
              name="leave-alcohol"
              id="leave-alcohol"
              class="btn"
              value="leave-alcohol"
            />
            Vi lämnar tillbaka överbliven alkohol - 1000kr</label
          >
          <label for="buy-ice"
            ><input
              v-model="event.extras"
              type="checkbox"
              name="buy-ice"
              id="buy-ice"
              class="btn"
              value="buy-ice"
            />
            Vi köper in is - 500kr</label
          >
        </p>
      </div>
      <p class="form-control">
        <label>Mer info</label>
        <textarea
          v-model="event.moreInfo"
          name="moreInfo"
          :class="{ filled: event.moreInfo }"
          placeholder="tex. typ av event (Firmafest, Studentskiva, Bröllop)"
        />
      </p>
    </div>

    <hr class="border-primary-600 mt-4" />

    <p class="form-control mt-6">
      <button class="btn w-full" type="submit" :disabled="!formIsFilled">
        Skicka offertförfrågan
      </button>
    </p>
  </form>
</template>

<script>
export default {
  data() {
    return {
      event: {
        place: '',
        date: '',
        time: '',
        email: '',
        tel: '',
        size: '',
        staff: {
          waiter: '0',
          bartender: '0',
          dj: '0'
        },
        extras: [],
        moreInfo: '',
      },
    }
  },
  computed: {
    formIsFilled() {
      return (
        !!this.event.place &&
        !!this.event.date &&
        !!this.event.time &&
        !!this.event.email &&
        !!this.event.tel &&
        !!this.event.size
      )
    },
  },
  methods: {
    // encode(data) {
    //   return Object.keys(data)
    //     .map(
    //       key => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
    //     )
    //     .join('&')
    // },
    // handleSubmit() {
    //   // TODO: Add additional guests
    //   fetch('/', {
    //     method: 'POST',
    //     headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    //     body: this.encode({
    //       'form-name': 'rsvp',
    //       ...this.offer
    //     })
    //   })
    //     .then(() => this.$router.push('thanks'))
    //     .catch(() => this.$router.push('404'))
    // }
  }
}
</script>
