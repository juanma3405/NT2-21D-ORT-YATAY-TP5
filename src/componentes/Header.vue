<template>
  <section
    class="src-componentes-header"
    :style="{ backgroundColor: headerBackgroundColor }"
  >
    <h1>
      The Great <br />
      <span id="colorDisplay">{{ headerNameColor }}</span>
      <br />
      Guessing Game
    </h1>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-componentes-header',
    props: ['headerNameColor','headerBackgroundColor'],
    mounted () {

    },
    data () {
      return {
      
      }
    },
    methods: {
   
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
.src-componentes-header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}

#colorDisplay {
  font-size: 200%;
}

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
</style>
