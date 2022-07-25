<template>
  <div>
    <label for="Ip" class="title">Ingrese su ip</label>
    <p></p>
    <input
      id="Ip"
      type="text"
      placeholder="ej: 157.100.91.131"
      v-model="ipAdress"
    />

    <button v-on:click="obtenerIp" class="title">Buscar</button>
  </div>
  <p></p>
  <div>
    <table v-if="type" class="ipTable">
      <tr>
        <td><label class="title">Ip: </label></td>
        <td>
          <label>{{ ipAdress }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Tipo de IP: </label></td>
        <td>
          <label>{{ type }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Continente : </label></td>
        <td>
          <label>{{ continent }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">País : </label></td>
        <td>
          <label>{{ country }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Región : </label></td>
        <td>
          <label>{{ region }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Ciudad: </label></td>
        <td>
          <label>{{ city }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Organización: </label></td>
        <td>
          <label>{{ org }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Proveedor de Internet: </label></td>
        <td>
          <label>{{ isp }}</label>
        </td>
      </tr>
      <tr>
        <td><label class="title">Imagen :</label></td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td>
          <div class="imagen">
            <img v-if="img" :src="img" alt="no se encontró" />
          </div>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "Ip",
  data() {
    return {
      ipAdress: "",
      type: null,
      continent: null,
      country: null,
      region: null,
      city: null,
      org: null,
      isp: null,
      img: null,
    };
  },
  methods: {
    async consultaIp() {
      const {
        type,
        continent,
        country,
        region,
        city,
        connection: { org },
        connection: { isp },
        flag: { img },
      } = await fetch("https://ipwho.is/" + this.ipAdress).then((r) =>
        r.json()
      );
      this.type = type;
      this.continent = continent;
      this.country = country;
      this.region = region;
      this.city = city;
      this.org = org;
      this.isp = isp;
      this.img = img;
    },
    obtenerIp() {
      this.consultaIp();
    },
  },
};
</script>

<style scoped>
label {
  display: block;
  color: white;
  font-size: 20px;
  margin-top: 20px;
}

.title {
  font-weight: bolder;
}

.imagen {
  display: flexbox;
  align-items: center;
}

.ipTable {
  margin: auto;
}

input {
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  width: 200px;
  margin-bottom: 10px;
  cursor: pointer;
}
</style>