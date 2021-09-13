<template>
 <div id="app">
    <div class="Center">
      <Header />
      <Base />
    </div>
</div>

</template>

<script>
import Header from './components/Header.vue'
import Base from './pages/Base.vue'

export default {
  name: 'App',
  components: { Header, Base }
}
</script>

<style lang="scss">
</style>
