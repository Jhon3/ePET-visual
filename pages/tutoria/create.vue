<template>
  <div>
    <div>
      <b-card header="Disciplinas cadastradas">
        <!-- TODO::remover esse style -->
        <div>
        <form @submit="submitForm">
          <div class="form-group">
            <label for="exampleFormControlInput1">Tema</label>
            <input type="text" class="form-control" v-model="tema" />
          </div>
          <div class="form-group">
            <label for="exampleFormControlInput1">Código</label>
            <input type="text" class="form-control" v-model="codMateria" />
          </div>
          <div class="form-group">
            <label for="exampleFormControlInput1">Local</label>
            <input type="text" class="form-control" v-model="local" />
          </div>
          <div class="form-group">
            <label for="exampleFormControlInput1">Data</label>
            <input type="date" class="form-control" v-model="data" />
          </div>

          <b-form-group label="Anexo">
                <label><input type="file" id="file" ref="file" v-on:change="handleFileUpload()"/>
                </label>

              </b-form-group>
          
        
        <div class="form-group">
            <button type="submit">Enviar</button>
        </div>
        </form>
        </div>
        
      </b-card>
    </div>
  </div>
</template>

<script>
import axios from "../../axios";

export default {
  name: "dashboard",
  /* TODO:: Esse layout será apresentado tanto pro petiano quando pro coordenador
  depois será necessário uma lógica pra chamar o layout dependendo do tipo de usuário
  logado. No momento trabalharei apenas com os petianos. */
  layout: "menu/petiano",
  data() {
    return {
      tema: '',
      local: '',
      codMateria: '',
      file: '',
      data: '',
      disciplinas: [],
      currentPessoa:[],
      currentPetiano:[],
      currentPage: 1,
      fields: [
        { key: "codigo", sortable: true },
        { key: "nome", sortable: true },
        { key: "actions", sortable: true },
      ]
    };
  },
  mounted() {
    axios.get("pessoas-usuario").then(res => {
      this.currentPessoa = res.data;
      if(res.data.tipo_usuario.nome != "petiano" && res.data.tipo_usuario.nome != "tutor")
      {
        this.$router.push("/");
      }
    }).finally( () =>{
      axios.get("petianos-pessoa/"+this.currentPessoa.idPessoa).then(res2 => {
        this.currentPetiano = res2.data;
        console.log(this.currentPetiano);
      });
      }
    );
    console.log("petianos-pessoa/");
  },
  methods: {
    submitForm(e){
      /*this.$router.push(
        {
          path: 'edit/',
          query  : {"id": id,
                    "nome": nome,
                    "codigo":codigo}
        }
      )*/
      let idSalvo = null;
      console.log("Clicou")
      console.log("tutoria-cadastro/" + this.currentPetiano.idPetiano +"/"+ this.codMateria +"/");
      console.log("Data = " + this.tema + "\nLocal = " + this.local)
      axios.post("/tutoria-cadastro/" + this.currentPetiano.idPetiano +"/" + this.codMateria + "/", {
        tema: this.tema,
        local: this.local,
        data: this.data
      }).then(res => {
        // para não ter que atualizar os eventos em tempo real forçarei a página a atualizar
        alert('Tutoria cadastrada com sucesso');
        console.log(res)
        idSalvo = res.data.idTutoria;
        //let vm = this;
        //setTimeout(function(){
        //  location.reload()
        //}, 1500)
      }).catch( err => {console.log(err)});

      /*const toBase64 = file => new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.readAsDataURL(file);
        reader.onload = () => resolve(reader.result);
        reader.onerror = error => reject(error);
      });
      let arquivo = toBase64(this.file);*/

      /*let formData = new FormData(); 
      formData.append('file', this.file);      
      let arquivo = new URLSearchParams(formData).toString();
      */
      
      /*axios.post("/anexos-tutoria-cadastro/12", {
        anexos : arquivo
        }).then(res => {
          alert('Anexo cadastrado com sucesso.')
        }).catch(err => {console.log(err)});
      console.log("Arquivo = " + arquivo)
      console.log("FUNCIONOU!")*/

    },
    handleFileUpload(){
      this.file = this.$refs.file.files[0];
    },
  }
  /*methods: {
    del(id, rowId){
      axios.delete("eventos-remove/" + id).then(() => {
        this.disciplinas.splice(rowId, 1);
        alert('Evento removido com sucesso');
      });
    },
    ativar(id){
      axios.post("eventos-ativar/" + id).then(() => {
        // para não ter que atualizar os eventos em tempo real forçarei a página a atualizar
        alert('Evento ativado com sucesso');
        let vm = this;
        setTimeout(function(){
          location.reload()
        }, 1500)
      });
    }
  }*/
};
</script>