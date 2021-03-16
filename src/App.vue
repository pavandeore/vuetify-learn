<template>
  <div>
    <NavBar />
    <div id="beer-wraper">
      <BeerComponent />
    </div>
  </div>
</template>

<script>

import NavBar from './components/Navbar';
import BeerComponent from './components/BeerComponent';

export default {
  name: 'App',
  components: {
    BeerComponent,
    NavBar
  }
}
</script>

<style>

*{
  margin:0;
  padding:0;
  font-family: verdana;
  cursor: url('./assets/beer.png'), auto;
}
#beer-wraper > div{
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
}

</style>
