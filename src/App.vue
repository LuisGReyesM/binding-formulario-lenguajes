<template>
  <div id="app">
    <form>
      <div>
        <label>Título:</label>
        <input type="text" name="titulo" v-model="tarjeta.titulo" />
      </div>
      <hr>
      <div>
        <label>Emoji </label>
        <select v-model="tarjeta.emoji">
          <option v-for="emoji in emojis" :value="emoji">{{ emoji }}</option>
        </select>
      </div>
      <hr>
      <div>
  <label>Apreciación: </label>
  <ul class="apreciacion-lista">
    <li>
      <input type="radio" value="Regular" name="apreciacion" v-model="tarjeta.apreciacion" />
      Regular
    </li>
    <li>
      <input type="radio" value="Bien" name="apreciacion" v-model="tarjeta.apreciacion" />
      Bien
    </li>
    <li>
      <input type="radio" value="Muy Bien" name="apreciacion" v-model="tarjeta.apreciacion" />
      Muy bien
    </li>
    <li>
      <input type="radio" value="Increible" name="apreciacion" v-model="tarjeta.apreciacion" />
      Increíble
    </li>
  </ul>
</div>


      <hr>
      <div>
        <label>Competencias aprendidas</label>
        <div class="competencias-grid">
          <div v-for="competencia in competencias" :key="competencia" class="competencia-item">
            <label>
              <input type="checkbox" v-model="seleccionadas" :value="competencia" />
              {{ competencia }}
            </label>
          </div>
        </div>
      </div>

      <hr>
      <div>
        <label for="opinion"> Opinión</label>
        <textarea name="opinion" v-model="tarjeta.opinion" rows="2" cols="50"></textarea>
      </div>
    </form>

    <div class="carnet">
      <div>
        {{ tarjeta.emoji }}
      </div>
      <h2>{{ tarjeta.titulo }} </h2>

      <div>
        <h2 v-if="tarjeta.apreciacion">Y me parece {{ tarjeta.apreciacion }}</h2>
      </div>
      <div>
        <p>{{ obtenerCompetenciasComoCadena() }}</p>
      </div>
      <div>
        <h2>{{ tarjeta.opinion }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      tarjeta: {
        titulo: "",
        emoji: "",
        apreciacion: "",
        competencia: "",
        opinion: "",
      },
      competencias: [
        "Morfología de un componente",
        "Directivas",
        "One-Way y Two Way data binding",
        "Estado",
        "El patrón de diseño MVVM"
      ],
      emojis: ["😡", "😂"],
      seleccionadas: [],
    };
  },
  methods: {
    obtenerCompetenciasComoCadena() {
      return this.seleccionadas.join(', ');
    },
  },
};
</script>

<style>
* {
  margin: 0;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60vh;
  font-size: 10px;
  font-family: sans-serif;
}

#app {
  display: flex;
  gap: 40px;
}

.apreciacion-lista {
  display: flex;
  gap: 3px;
  list-style: none; 
  padding: 0;
}

.apreciacion-lista li {
  display: flex;
  align-items: center; 
  padding: 3px;  
}

form {
  padding: 18px;
  border-radius: 20px;
  border: ridge 1px;
  box-shadow: 1px 1px 1px 1px gray;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  gap: 15px;
  justify-content: center;
}

form div {
  display: grid;
  grid-template-columns: 100px 250px;
  align-items: left;
  gap: 5px;
}

form div label input {
  text-align: left;
}



.carnet {
  width: 400px;
  height: 230px;
  background: #1c1a1e;
  color: white;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0px 0px 10px 2px black;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  
}

.carnet>div,
.carnet>h2,
.carnet>p {
  margin: 10px 0; 
}

h2 {
  font-size: 10px;
  margin-bottom: 15px;
  text-shadow: 0px 0px 1px gold;
  font-family: Times;
}


footer {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  font-weight: bold;
  font-size: 18px;
  text-transform: uppercase;
  font-style: italic;
}
</style>
