<template>
  <div>
    <div>
      <b-card header="Tutores cadastrados">
         <!--TODO::remover esse style -->
        <a
          class="btn btn-sm btn-primary float-right"
          style="color: white"
          href="tutoria/create"
        >Adicionar Tutoria</a>
        <b-table
          responsive="sm"
          :items="tutorias"
          :current-page="currentPage"
          :bordered="true"
          :per-page="10"
          :fields="fields"
        >
          <template v-slot:cell(ativo)="row">
            <div class="form-check">
              <input type="checkbox" class="form-check-input" :checked="row.item.ativo" disabled>
              </div>
          </template>
          <template v-slot:cell(actions)="row">
            <b-button @click="del(row.item.tutoria.idTutoria, row.index)" class="btn btn-sm btn-danger">Deletar</b-button>
            <b-button
                  @click="downloadfile(row.item)"
                  class="btn btn-sm"
                >Download</b-button>
          </template>
        </b-table>
        
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
      tutorias: [],
      currentPage: 1,
      fields: [
        { key: "tutoria.disciplina.nome", label:"Nome da Disciplina", sortable: true },
        { key: "tutoria.disciplina.codigo", label:"Código da Disciplina", sortable: true },
        { key: "tutoria.petiano.pessoa.nome", label:"Nome do Petiano", sortable: true },
        { key: "actions", sortable: true },
      ]
    };
  },
  mounted() {
    axios.get("/anexos-tutoria").then(res => {
      this.tutorias = res.data;
      
    }).catch(err => {console.log(err)});
  },
  methods: {
    del(id, rowId){
      console.log(id);
      axios.delete("tutoria-remove/" + id).then(() => {
        this.tutorias.splice(rowId, 1);
        alert('Tutoria removido com sucesso');
      });
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