<template>
  <div class="main text-center flex flex-col items-center justify-center mb-16">
    <logo />
    <h2 class="text-xl mb-6">Hyr in barpersonal till event</h2>
    <img src="/img/bartender.jpg" title="bartender pouring a drink" class="w-full h-auto max-w-3xl rounded-xl"/>
    <h3 class="title mt-12">Offertförfrågan</h3>
    <form-event/>
  </div>
</template>

<script>
import Logo from '~/components/general/Logo.vue'
import FormEvent from '~/components/forms/FormEvent.vue'

export default {
  components: {
    Logo,
    FormEvent
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }]
    }
  }
}
</script>
