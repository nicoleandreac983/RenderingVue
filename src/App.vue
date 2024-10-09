<script>
export default {
  name: "App",
  data() {
    return {
      color: "",
      colorTexto: "",
      mostrarlos: ["Mostrar texto"],
      selectedMostrarlos: [],
      mostrarTexto: "",
      borde: 1,
      tipografia: "",
      opaco: false,
      tamanoLetra: "",

    };
  },
};
</script>

<template>
  <div class="contenedor">
    <form class="form">
      <div class="colores">
        <label class="labels">Color de fondo</label>
        <input id="col" v-model="color" />

        <label class="labels">Color de texto</label>
        <input id="col" v-model="colorTexto" />

        <label class="labels">Mostrar texto</label>
        <div class="form-check" v-for="mostrar in mostrarlos" :key="mostrar">
          <input class="form-check-input" type="checkbox" :value="mostrar" v-model="selectedMostrarlos" />
          {{ mostrar }}
        </div>

        <label class="labels">Contenido Textual</label>
        <textarea v-model="mostrarTexto"></textarea>

        <label class="labels">Borde</label>
        <input class="form-range" type="range" min="1" max="100" v-model="borde" />

        <label class="labels">Tipografia</label>
        <select class="select form-select " aria-label="Default select example" v-model="tipografia">
          <option value="">Normal</option>
          <option value="bold">Negrita </option>
          <option value="italic">Cursiva </option>
          <option value="underline">Subrayada </option>
        </select>

        <label class="labels">
          Opaco
          <input class="form-check-input" type="checkbox" v-model="opaco" />
        </label>

        <label class="labels">Tamaño de letra</label>
        <div class="tamanos-letra form-check">
          <label>
            <input class="form-check-input" type="radio" value="chico" v-model="tamanoLetra" />Chico
          </label>
          <div class="form-chek">
            <label >
              <input class="form-check-input" type="radio" value="mediano" v-model="tamanoLetra" />Mediano
            </label>
          </div>
          <div class="form-check">
            <label >
              <input class="form-check-input" type="radio" value="grande" v-model="tamanoLetra" />Grande
            </label>
          </div>
        </div>
      </div>
    </form>
    <div class="resultado">
      <div v-show="color" :style="{ backgroundColor: color,color: colorTexto, borderRadius: borde + '%',}"class="box">
        <p v-if="selectedMostrarlos.length > 0" :style="{fontWeight: tipografia === 'bold' ? 'bold' : 'normal',fontStyle: tipografia === 'italic' ? 'italic' : 'normal',
            textDecoration: tipografia === 'underline' ? 'underline' : 'none',opacity: opaco ? 0.5 : 1,
            fontSize:
              tamanoLetra === 'chico'
                ? '10px'
                : tamanoLetra === 'mediano'
                ? '30px'
                : tamanoLetra === 'grande' 
                ? '50px' 
                : '40px',
          }">
          {{ mostrarTexto }}
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.contenedor {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap; 
  width: 100%; 
  padding: 20px;
  color: wheat;
}

.form {
  width: 25%; 
  height: 650px;
  background-color: #5012c3; 
  border: 1px solid #000; 
  padding: 20px; 
  border-radius: 8px; 
  box-sizing: border-box;

}

.resultado {
  width: 30%; 
  display: flex;
  justify-content: center;
  align-items: flex-end;
  margin-right: 300px
}

.box {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  width: 100%; 
  height: 200px;
  border: 1px solid #000;
  margin-top: 90px;
  padding: 10px; 
  border-radius: 8px 8px 0 0; 
}

.select {
  width: 200px;
}

textarea {
  width: 200px;
  height: 50px;
  margin-top: 10px;
  margin-bottom: 10px;
}

p {
  margin-bottom: 80px;
  text-align: center;

}

.labels {
  margin-top: 5px;
  margin-bottom: 5px;
}

#col {
  width: 200px;
  height: 30px;
  margin-top: 10px;
}
.colores {
  display: flex;
  flex-direction: column;
}

.labels {
  margin-top: 5px;
  margin-bottom: 5px;
}


</style>
