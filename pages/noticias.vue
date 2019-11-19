<template>
  <div class="animated fadeIn">
    <div>
      <b-row>
        <b-col md="12">
          <b-card header="Criar notícia">
            <b-form>
              <b-form-group label="Título">
                <b-form-input required placeholder="Insira o título" v-model="noticia.titulo"></b-form-input>
              </b-form-group>
              <b-form-group label="Corpo">
                <b-form-input required placeholder="Insira o título" v-model="noticia.corpo"></b-form-input>
              </b-form-group>
              <b-form-group label="Data de Início">
                <b-form-input type="date" required placeholder="Insira o título" v-model="noticia.data_inicio"></b-form-input>
              </b-form-group>
              <b-form-group label="Data de Fim">
                <b-form-input type="date" required placeholder="Insira o título" v-model="noticia.data_fim"></b-form-input>
              </b-form-group>

              <b-form-group label="Anexo">
                <label><input type="file" id="file" ref="file" v-on:change="handleFileUpload()"/>
                </label>

              </b-form-group>

              <b-button @click="sendNoticia()" type="button" variant="primary">Cadastrar</b-button>
            </b-form>
          </b-card>
        </b-col>
      </b-row>
      <b-row>
        <b-col md="12">
          <b-card header="Notícias">
            <b-table
              class="mb-0 table-outline"
              responsive="sm"
              :current-page="currentPage"
              hover
              :items="tableItems"
              :fields="tableFields"
              :per-page="10"
              head-variant="light"
            >
              <template v-slot:cell(actions)="row">
                <b-button
                  @click="removerNoticias(row.item.idNoticia)"
                  class="btn btn-sm btn-danger"
                >Deletar</b-button>
                <b-button
                  @click="downloadfile(row.item)"
                  class="btn btn-sm"
                >Download</b-button>
              </template>
            </b-table>
            <nav>
              <b-pagination
                :total-rows="tableItems.length"
                :per-page="10"
                v-model="currentPage"
                prev-text="Anterior"
                next-text="Próximo"
                hide-goto-end-buttons
              />
            </nav>
          </b-card>
        </b-col>
      </b-row>
    </div>
    <div class="row">Nenhum evento cadastrado.</div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import axios from "axios";

export default {
  //middleware: 'auth',
  name: "admin",
  layout: "adminLayout",
  components: {},
  data: function() {
    return {
      file: '',
      noticias: [],
      noticia: {
        titulo: "",
        corpo: "",
        data_inicio: "",
        data_fim: ""
      },
      selected: "Month",
      currentPage: 1,
      tableItems: [],
      tableFields: [
        { key: "inicio_exibicao", label: "Inicio"},
        { key: "limite_exibicao", label:"Fim" },
        { key: "titulo", label: "Titulo" },
        { key: "corpo", label: "Notícia" },
        { key: "actions", label: "Ações" },
      ]
    };
  },
  computed: {
    ...mapGetters(["loggedInUser"])
  },
  mounted() {
    this.getNoticias();
  },
  methods: {
    async logout() {
      await this.$auth.logout();
    },
    async getNoticias() {
      await axios
        .get("http://localhost:8080/api/noticia", {
          auth: { username: "h@email.com", password: "password" }
        })
        .then(res => {
          let result = res.data.content;
          this.tableItems = result;
        });
    },
    async removerNoticias(id) {
      await axios
        .delete(`http://localhost:8080/api/noticia-remove/${id}`, {
          auth: { username: "h@email.com", password: "password" }
        })
        .then(res => this.getNoticias());
    },
    async sendNoticia() {

      let formData = new FormData();
      formData.append('file', this.file);
      let arquivo = new URLSearchParams(formData).toString();
      let noticia_arq = null;

      await axios
        .post(
          "http://localhost:8080/api/noticia-cadastro/1",
          {
            titulo: this.noticia.titulo,
            corpo: this.noticia.corpo,
            inicio_exibicao: this.noticia.data_inicio,
            limite_exibicao: this.noticia.data_fim
          },
          { auth: { username: "h@email.com", password: "password" } }
        )
        .then(res => {noticia_arq = res; console.log(res);});

        await axios.post(`http://localhost:8080/api/anexos-noticia-upload/${noticia_arq._id}`, {
          anexos: arquivo
        });
      
      this.getNoticias();

      this.noticia.titulo = "";
      this.noticia.corpo = "";
      this.noticia.data_inicio = "";
      this.noticia.data_fim = "";
      this.file = null;

      console.log(this.noticia.corpo);
    },
    handleFileUpload(){
      this.file = this.$refs.file.files[0];
    },
    downloadfile(file){
      window.open('data:text/html;charset=utf-8,' +
    encodeURIComponent(
        file.anexos
    )
)
    }
  }
};
</script>