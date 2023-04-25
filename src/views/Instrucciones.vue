<script>
import emailjs from 'emailjs-com'
export default {
  data() {
    return {
      stepCounter: 0,
      answer1: '',
      answer2: '',
      answer3: '',
      answer4: '',
      answer5: [],
      answer6: '',
      answer7: '',
      answer8: '',
      answer9: '',
      answer10: '',
      answer11: '',
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
    },
    sendForm() {}
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<template>
    <v-container class="text-center text-white">
      <div v-if="stepCounter === 0">
        <h1 class="text-h4 text-md-h1 font-weight-bold mt-md-16">Hola Renee:)</h1>
        <h2 class="mt-8 text-md-h2">¿Estás lista?</h2>
      </div>
      <div v-if="stepCounter === 1">
        <h1 class="text-h5 text-md-h1 font-weight-bold mt-md-16 mb-md-12">¿Recuerdas el plan de cena sorpresa?</h1>
        <br />
        <h2 class="text-h6 text-md-h3 mb-6 mb-md-12">Instrucciones:</h2>
        <p class="text-body-1 text-md-h6 text-left text-yellow">
          Para llevarlo a cabo este plan necesito que contestes una pequeña encuesta esto para
          conocer:
        </p>
        <ol class="text-body-2 text-md-body-1 text-left mt-10">
          <li>Tus gustos</li>
          <li>Temática</li>
          <li>Habilidades en cocina</li>
          <li>Y otras sorpresas ;)</li>
        </ol>
      </div>

      <div v-if="stepCounter === 2">
        <h1 class="text-h5 text-md-h1 mb-6 mb-md-12 mt-md-16 font-weight-bold">Sobre tu comida favorita</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 mb-3 mb-md-8">1.-¿Cuál es tu comida favorita?</h2>
            <v-text-field
              v-model="answer1"
              class="text-body-1"
              name="answer1"
              label="Tal vez son los tacos con Matcha?"
              required
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h6 text-md-h3 my-3 mb-md-8">2.-¿Sabés cómo cocinarlo?</h2>
            <v-select
              v-model="answer2"
              class="text-body-1"
              name="answer2"
              label="Se vale decir que no"
              :items="['Si', 'No', 'Se me quema aveces']"
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 3">
        <h1 class="text-h5 text-md-h1 mb-md-12 mb-3 mb-md-8 mt-md-16 font-weight-bold">Sobre tu postre favorito</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 mb-3 mb-md-8">3.-¿Cuál es tu postre favorito?</h2>
            <v-text-field
              v-model="answer3"
              class="text-body-1"
              name="answer3"
              label="Tal vez son los frappe con Matcha?"
              required
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h6 text-md-h3 my-3 mb-md-8">4.-¿Sabés cómo hacerlo?</h2>
            <v-select
              v-model="answer4"
              class="text-body-1"
              name="answer4"
              label="Se vale decir que no"
              :items="['Si', 'No', 'Se me quema aveces']"
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 4">
        <h1 class="text-h5 text-md-h1 mb-md-12 mt-md-16 font-weight-bold">Regiones de cómida</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 my-3 mb-md-8">5.-¿Cual region o regiones de comida te gustaría preparar?</h2>
            <v-select
              v-model="answer5"
              class="text-body-1"
              name="answer5"
              label="Puedes seleccionar varias opciones pero escoge max 3 opciones porfi"
              multiple
              :items="[
                'Mexicana',
                'Italiana',
                'Japonesa',
                'China',
                'Colombiana',
                'Tailandesa',
                'Americana',
                'Colombiana',
                'Española',
                'Francesa'
              ]"
              hint="Te recuerdo que max 3 opciones D:"
              persistent-hint
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 5">
        <h1 class="text-h5 text-md-h1 mb-md-12 mb-3 mt-md-16 font-weight-bold">Siempre he deseado...</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 mb-3 mb-md-8">
              6.-¿Platillo que tienes ganas de preparar y no has hecho?
            </h2>
            <v-text-field
              v-model="answer6"
              class="text-body-2"
              name="answer6"
              label="Por ejemplo: crepas o empanadas saladas"
              required
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h6 text-md-h3 my-3 mb-md-8">
              7.-¿Postre que tienes ganas de preparar y no has hecho?
            </h2>
            <v-text-field
              v-model="answer7"
              class="text-body-1"
              name="answer7"
              label="Por ejemplo: macarons o galletas estilo cotsco"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 6">
        <h1 class="text-h5 text-md-h1 mb-md-12 mt-md-16 font-weight-bold">Alergias y manguitos</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 my-6">
              8.-¿Eres alergica a algún alimento además de la cascara de mango?
            </h2>
            <v-text-field
              v-model="answer8"
              class="text-body-1"
              name="answer8"
              label="Ya habíamos hablado de esto pero mejor prevenir"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 7">
        <h1 class="text-h5 font-weight-bold mb-md-12 text-md-h1 mt-md-16">No me gusta</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 my-6 mb-md-8">
              9.-¿Aparte de los frijoles, que otro alimento no te gusta o no te agrada mucho?
            </h2>
            <v-text-field
              v-model="answer9"
              class="text-body-1"
              name="answer9"
              label="Tip: Se vale decir que el Matcha realmente no te gusta"
              required
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 8">
        <h1 class="text-h5 text-md-h1 mb-md-12 font-weight-bold mt-md-16">Si hay sol hay playa... y albercas</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 mt-3 mb-md-8">10.-¿Te gustan las albercas?</h2>
            <v-select
              v-model="answer10"
              class="text-body-1"
              name="answer10"
              label="Nunca olvides el bloqueador"
              :items="['Si', 'No']"
            />
          </v-col>
          <v-col cols="12">
            <h2 class="text-h6 text-md-h3 my-3 mb-md-8">11.-¿Y los Jacuzzis?</h2>
            <v-select
              v-model="answer11"
              class="text-body-1"
              name="answer11"
              label="Za za za jacuzzi za"
              :items="[
                'Si',
                'No',
                'Nunca he estado en uno pero me gustaria',
                'Nunca he estado en uno pero me gustaria estar en uno!'
              ]"
            />
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 9">
        <h1 class="text-h5 text-md-h1 mb-md-12 font-weight-bold mt-md-16">Terminar encuesta</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 mt-3">
              Al dar clic en terminar se enviaran tus resultados, si quieres
              cambiar alguna respuesta da clic en anterior
            </h2>
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 10">
        <h1 class="text-h4 text-md-h1 mb-md-12 font-weight-bold mt-md-16">Oh no... Algo salio mal</h1>
        <v-row>
          <v-col>
            <h2 class="text-h5 text-md-h3 my-6">Parece que faltaba una pregunta 😅</h2>
            <p class="text-body-1">Por suerte sé cual es da clic en siguiente para poderla cargar 🤓</p>
          </v-col>
        </v-row>
      </div>

      <div v-if="stepCounter === 11">
        <h1 class="text-h4 text-md-h1 mb-md-12 font-weight-bold mt-md-16">La pregunta final es:</h1>
        <v-row>
          <v-col>
            <h2 class="text-body-2 text-md-h3 mt-3 mb-md-8">
              12.-¿01110001 01110101 01101001 01100101 01110010 01100101 01110011 00100000 01110011
              01100101 01110010 00100000 01101101 01101001 00100000 01101110 01101111 01110110
              01101001 01100001 ?
            </h2>
            <v-select
              v-model="secondName2"
              class="text-body-1"
              label="Igual y puedes catafixiar"
              :items="['Si', 'No', 'Quiero catafixiar']"
            />
          </v-col>
        </v-row>
        <h2 class="text-body-1 text-left text-md-h3 mt-3">
          Lo siento Renee :( Erick es medio menso y no supo programar esta parte ¿Por qué no le
          preguntas a él cuál es esta pregunta? igual y si se acuerda :) <br> Mientras darle al botón de abajo de Terminar y yo guardo tus respuestas ;)
        </h2>
      </div>

      <div v-if="stepCounter === 12">
        <h1 class="text-h5 text-md-h1 mb-md-12 font-weight-bold mt-md-16">Esas fueron tus respuestas</h1>
        <v-row>
          <v-col>
            <h2 class="text-h6 text-md-h3 my-6">Tomale Screen y mandaselo a Erick porfi</h2>
            <ol class="text-body-2 text-left">
              <li>Siempre he deseado...: {{ answer1 }}</li>
              <li>¿Sabés cómo cocinarlo?: {{ answer2 }}</li>
              <li>Sobre tu postre favorito: {{ answer3 }}</li>
              <li>¿Sabés cómo hacerlo?: {{ answer4 }}</li>
              <li>Regiones de cómida: {{ answer5 }}</li>
              <li>
                ¿Cuál es el platillo siempre has tenido ganas de prepararlo y aun no lo has hecho?:
                {{ answer6 }}
              </li>
              <li>
                ¿Cuál es el postre siempre has tenido ganas de prepararlo y aun no lo has hecho?:
                {{ answer7 }}
              </li>
              <li>¿Eres alergica a algún alimento además de la cascara de mango?: {{ answer8 }}</li>
              <li>
                ¿Aparte de los frijoles, que otro alimento no te gusta o no te agrada mucho?:
                {{ answer9 }}
              </li>
              <li>¿Te gustan las albercas?: {{ answer10 }}</li>
              <li>¿Y los Jacuzzis?: {{ answer11 }}</li>
              <li>Esa se la contestaste a Erick</li>
            </ol>
          </v-col>
        </v-row>
      </div>
      <v-row>
        <v-col cols="6" v-if="stepCounter > 1 && stepCounter <= 9">
          <v-btn class="text-body-1 text-md-h6 text-white mt-8 mr-16" color="#4f545c" size="large" @click="backStep()">
            Anterior
          </v-btn>
        </v-col>
        <v-col :cols="stepCounter == 0 || stepCounter == 1 || stepCounter == 10 ? 12 : 6" v-if="stepCounter !== 9 && stepCounter < 11">
          <v-btn class="text-body-1 text-md-h6 text-white mt-8" color="#4f545c" size="large" @click="nextStep()">
            Siguiente
          </v-btn>
        </v-col>
        <v-col cols="6" v-if="stepCounter === 9">
          <v-btn class="text-body-1 text-md-h6  text-white mt-8" color="#4f545c" size="large" @click="nextStep()">
            Terminar
          </v-btn>
        </v-col>
        <v-col cols="12" v-if="stepCounter === 11">
          <div class="text-center">
            <button
              @click="nextStep()"
              class="button-64 text-white mt-8 text-center center"
              color="#4f545c"
              size="large"
            >
              Terminar
            </button>
          </div>
        </v-col>
      </v-row>
    </v-container>
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
  font-size: 16px;
  justify-content: center;
  line-height: 1em;
  max-width: 100%;
  min-width: 140px;
  padding: 12px;
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
