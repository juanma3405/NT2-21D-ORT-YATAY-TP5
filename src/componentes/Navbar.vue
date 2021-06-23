<template>
  <section class="src-componentes-navbar">
    <button id="reset" @click="$emit('eventRestart')">{{ rb }}</button>
    <span id="message"> {{ ms }} </span>

    <button id="easy" @click="easyMode()" :class="mode ? '' : 'selected'">
      easy
    </button>
    <button id="hard" @click="hardMode()" :class="mode ? 'selected' : ''">
      hard
    </button>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-componentes-navbar',
    props: ['rb','ms','mode'],
    mounted () {

    },
    data () {
      return {
    
      }
    },
    methods: {
      easyMode(){
        this.$emit('changeMode', false)
        },
    
        hardMode(){
        this.$emit('changeMode', true)  
        }

    },
    computed: {
    
    }
}


</script>

<style scoped lang="css">
.src-componentes-navbar {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}

#message {
  color: #000000;
  display: inline-block;
  width: 20%;
}

button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}

.selected {
  background-color: steelblue;
  color: white;
}
</style>
