<script>
export default {
  data() {
    return {
      stepCounter: 10,
      answer1: '',
      secondName2: []
    }
  },
  methods: {
    nextStep() {
      this.stepCounter++
      console.log(this.stepCounter)
    },
    backStep() {
      this.stepCounter--
      console.log(this.stepCounter)
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<template>
  <form
    action="https://formsubmit.co/ericksilvam97@gmail.com"
    method="POST"
    class="d-flex flex-column"
  >
    <v-container class="text-center text-white">
      <div v-if="stepCounter === 1">
        <h1 class="text-h1">¿Recuerdas el plan de ir a cocinar?</h1>
        <br />
        <h2 class="text-h3 my-6">Instrucciones:</h2>
        <p class="text-left">
          Para llevarlo a cabo necesito que contestes una pequeña encuesta esto para conocer:
        </p>
        <ol class="text-left">
          <li>Tus gustos</li>
          <li>Temática</li>
          <li>Habilidades en cocina</li>
          <li>Y otras sorpresas ;)</li>
        </ol>
      </div>

      <div v-if="stepCounter === 2">
        <h1 class="text-h1">Sobre tu comida favorita</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">1.-¿Cuál es tu comida favorita?</h2>
            <v-text-field v-model="firstname" label="Tal vez son los tacos con Matcha?" required />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h3 my-6">2.-¿Sabés cómo cocinarlo?</h2>
            <v-select
              v-model="secondName"
              label="Se vale decir que no"
              :items="['Si', 'No', 'Se me quema aveces']"
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 3">
        <h1 class="text-h1">Sobre tu postre favorito</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">3.-¿Cuál es tu postre favorito?</h2>
            <v-text-field
              v-model="firstname1"
              label="Tal vez son los frappe con Matcha?"
              required
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h3 my-6">4.-¿Sabés cómo hacerlo?</h2>
            <v-select
              v-model="secondName2"
              label="Se vale decir que no"
              :items="['Si', 'No', 'Se me quema aveces']"
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 4">
        <h1 class="text-h1">Regiones de cómida</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">5.-¿Cual region o regiones de comida te gustaría preparar?</h2>
            <v-select
              v-model="secondName2"
              label="Puedes seleccionar varias opciones pero escoge max 3 opciones porfi"
              multiple
              :items="[
                'Mexicana',
                'Italiana',
                'Japonesa',
                'China',
                'Francesa',
                'Americana',
                'Colombiana',
                'Española',
                'Tailandesa'
              ]"
              hint="Te recuerdo que max 3 opciones D:"
              persistent-hint
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 5">
        <h1 class="text-h1">Siempre he deseado...</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">
              6.-¿Cuál es el platillo siempre has tenido ganas de prepararlo y aun no lo has hecho?
            </h2>
            <v-text-field
              v-model="firstname4"
              label="Por ejemplo: crepas o empanadas saladas"
              required
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h3 my-6">
              7.-¿Cuál es el postre siempre has tenido ganas de prepararlo y aun no lo has hecho?
            </h2>
            <v-text-field
              v-model="firstname4"
              label="Por ejemplo: macarons o galletas estilo cotsco"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 6">
        <h1 class="text-h1">Alergias y manguitos</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">
              8.-¿Eres alergica a algún alimento además de la cascara de mango?
            </h2>
            <v-text-field
              v-model="firstname4"
              label="Ya habíamos hablado de esto pero mejor prevenir"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 7">
        <h1 class="text-h1">No me gusta</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">
              9.-¿Aparte de los frijoles, que otro alimento no te gusta o no te agrada mucho?
            </h2>
            <v-text-field
              v-model="firstname4"
              label="Tip: Se vale decir que el Matcha realmente no te gusta"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 8">
        <h1 class="text-h1">Terminar encuesta</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">
              Al dar clic en terminar terminará la encuesta y se enviaran tus resultados, si quieres
              cambiar alguna respuesta da clic en anterior
            </h2>
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 9">
        <h1 class="text-h1">Oh no... Algo salio mal</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">Parece que faltaba una pregunta 😅</h2>
            <p>Por suerte sé cual es da clic en siguiente para poderla cargar 🤓</p>
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 10">
        <h1 class="text-h1">La pregunta final es:</h1>
        <v-row>
          <v-col>
            <h2 class="text-h3 my-6">
              10.-¿01110001 01110101 01101001 01100101 01110010 01100101 01110011 00100000 01110011
              01100101 01110010 00100000 01101101 01101001 00100000 01101110 01101111 01110110
              01101001 01100001 ?
            </h2>
            <v-select
              v-model="secondName2"
              label="Igual y puedes catafixiar"
              :items="['Si', 'No', 'Quiero catafixiar']"
            />
          </v-col>
        </v-row>
        <h2 class="text-h3 my-6">
          Lo siento Renee :( Erick es medio menso y no supo programar esta parte ¿Por qué no le
          preguntas a él cuál es esta pregunta? igual y si se acuerda :)
        </h2>
        <h2>Mientras darle al botón de abajo de Terminar y yo guardo tus respuestas ;)</h2>
      </div>

      <v-btn
        v-if="stepCounter !== 1 && stepCounter <= 8"
        class="text-white mt-8 mr-16"
        color="#4f545c"
        size="large"
        @click="backStep()"
      >
        Anterior
      </v-btn>
      <v-btn
        v-if="stepCounter !== 8 && stepCounter < 10"
        class="text-white mt-8"
        color="#4f545c"
        size="large"
        @click="nextStep()"
      >
        Siguiente
      </v-btn>
      <v-btn
        v-if="stepCounter === 8"
        class="text-white mt-8"
        color="#4f545c"
        size="large"
        @click="nextStep()"
      >
        Terminar
      </v-btn>
      <div class="text-center">
        <button
        v-if="stepCounter === 10"
        type="submit"
        class="button-64 text-white mt-8 text-center center"
        color="#4f545c"
        size="large"
      >
        Terminar
      </button>
      </div>
      
    </v-container>
  </form>
</template>

<style scoped>

/* CSS */
.button-64 {
  align-items: center;
  background-image: linear-gradient(144deg, #af40ff, #5b42f3 50%, #00ddeb);
  border: 0;
  border-radius: 8px;
  box-shadow: rgba(151, 65, 252, 0.2) 0 15px 30px -5px;
  box-sizing: border-box;
  color: #ffffff;
  font-family: Phantomsans, sans-serif;
  font-size: 20px;
  justify-content: center;
  line-height: 1em;
  max-width: 100%;
  min-width: 140px;
  padding: 20px;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
  cursor: pointer;
}

.button-64:active,
.button-64:hover {
  outline: 0;
}

.button-64 span {
  background-color: rgb(5, 6, 45);
  padding: 16px 24px;
  border-radius: 6px;
  width: 100%;
  height: 100%;
  transition: 300ms;
}

.button-64:hover span {
  background: none;
}

@media (min-width: 768px) {
  .button-64 {
    font-size: 24px;
    min-width: 196px;
  }
}
</style>
