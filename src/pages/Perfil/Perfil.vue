<template>
  <SiteTemplate>
    <span slot="menuesquerdo">
      <span v-if="user.image">
      <img
        :src="user.image"        
        class="responsive-img"
        alt="Background login"
      >
      </span>
      <span v-else>
          <img
        src="https://www.cyana.nl/images/UserFotos/Nieuws/avatar.jpg"        
        class="responsive-img"
        alt="Background login"
      >
      </span>
      <hr>
      <span v-if="this.usuario.image">
        <strong>Nova</strong>
      <img
        :src="this.usuario.image"        
        class="responsive-img"
        alt="this.usuario.name"
      >
      </span>
    </span>
    <span slot="principal">
      <h3 class="center">{{usuario.name}}</h3>

      <input type="text" placeholder="Nome" v-model="usuario.name">
      <input type="email" placeholder="E-mail" v-model="usuario.email">
      <div class="file-field input-field">
        <div class="btn">
          <span>Imagem</span>
          <input type="file" v-on:change="enviaImagem">
        </div>
        <div class="file-path-wrapper">
          <input class="file-path validate" type="text">
        </div>
      </div>
      <input type="password" placeholder="Senha" v-model="usuario.password">
      <input
        type="password"
        placeholder="Confirme Sua senha"
        v-model="usuario.password_confirmation"
      >      
      <button class="btn float-left" v-on:click="perfil()">Atualizar</button>
    </span>
  </SiteTemplate>
</template>

<script>
import SiteTemplate from "@/templates/SiteTemplate";
import Swal from 'sweetalert2';
import axios from "axios";

export default {
  name: "Perfil",
  data() {
    return {
      user: false,
      usuario: {
        name: "",
        email: "",
        password: "",
        password_confirmation: "",
        image: ""
      }
    };
  },

  components: {
    SiteTemplate
  },
  created() {
    let usuarioAux = sessionStorage.getItem("usuario");
    if (usuarioAux) {
      this.user = JSON.parse(usuarioAux);
      this.usuario.name = this.user.name;
      this.usuario.email = this.user.email;
      this.usuario.password = this.user.password;
      this.usuario.password_confirmation = this.user.password_confirmation;
     
    }
  },
  methods: {
    enviaImagem(e){
      let arquivo = e.target.files || e.dataTranfer.files;
      if(!arquivo.length){
        return;
      }
      let reader = new FileReader();

      reader.onload = e => {
      this.usuario.image = e.target.result;
      };
      reader.readAsDataURL(arquivo[0]);
     
    }, 
    message(title,type) {
    Swal.fire({
        title: title,
        type: type, 
        showConfirmButton: false,
        timer: 1500
    });
},
    perfil() {
      console.log("Botão cadastro precionado");

      axios
        .put(
          `http://localhost:8000/api/perfil`,
          {
            name: this.usuario.name,
            email: this.usuario.email,
            password: this.usuario.password,
            password_confirmation: this.usuario.password_confirmation,
            image: this.usuario.image
          },
          {
            headers: { authorization: "Bearer " + this.user.token }
          }
        )
        .then(response => {
          console.log(response);
          if (response.data) {
            //  Cadastro realizado com sucesso
            console.log(response.data);
             this.user = response.data;
            sessionStorage.setItem("usuario", JSON.stringify(this.user));
            console.log(response.data);
            this.usuario.image = false;
      console.log('teste false');            
            this.message('Perfil atualizado com sucesso!!!','success');
            this.$router.push("/perfil");
          } else {
            console.log("Erros na validação");
            let erros = "";
            for (let erro of Object.values(response.data)) {
              erros += erro + " ";
            }
            alert(erros);
          }
        })
        .catch(e => {
          console.log(e);
          alert("Erro !Tente Novamente mais tarde");
        });
    }
  }
};
</script>

