<template>
  <div class="animated fadeIn">
    <b-card>
      <b-row>
        <img src="../..//static/img/logo.png" style="height:200px; padding:20px; align: center;"/>
      </b-row>
    </b-card>
    <b-card>
      <b-row>
        <b-col sm="5">
          <h4 id="traffic" class="card-title mb-0">A plataforma perfeita para a sua escola</h4>
        </b-col>
        <p>Agora a sua escola pode ter a melhor plataforma de administração.<br />
        Muito mais do que uma simples plataforma, controle tutorias, eventos e disciplinas de uma maneira
        única, e muito mais a vim.
         No mundo atual, o consenso sobre a necessidade de qualificação não pode mais se dissociar do sistema de participação geral. A certificação de metodologias que nos auxiliam a lidar com a necessidade de renovação processual talvez venha a ressaltar a relatividade das diretrizes de desenvolvimento para o futuro. As experiências acumuladas demonstram que a percepção das dificuldades exige a precisão e a definição do sistema de formação de quadros que corresponde às necessidades. <br />

          Caros amigos, o acompanhamento das preferências de consumo cumpre um papel essencial na formulação de alternativas às soluções ortodoxas. Nunca é demais lembrar o peso e o significado destes problemas, uma vez que a consolidação das estruturas acarreta um processo de reformulação e modernização das condições financeiras e administrativas exigidas. O que temos que ter sempre em mente é que o aumento do diálogo entre os diferentes setores produtivos nos obriga à análise das formas de ação. Por conseguinte, a valorização de fatores subjetivos estimula a padronização do orçamento setorial. Assim mesmo, o desenvolvimento contínuo de distintas formas de atuação promove a alavancagem das condições inegavelmente apropriadas. <br />

          Acima de tudo, é fundamental ressaltar que a mobilidade dos capitais internacionais apresenta tendências no sentido de aprovar a manutenção dos métodos utilizados na avaliação de resultados. O incentivo ao avanço tecnológico, assim como a complexidade dos estudos efetuados aponta para a melhoria do retorno esperado a longo prazo. Pensando mais a longo prazo, o desafiador cenário globalizado facilita a criação de todos os recursos funcionais envolvidos. <br />

          Do mesmo modo, a hegemonia do ambiente político representa uma abertura para a melhoria do impacto na agilidade decisória. Desta maneira, o fenômeno da Internet ainda não demonstrou convincentemente que vai participar na mudança dos níveis de motivação departamental. É importante questionar o quanto a consulta aos diversos militantes prepara-nos para enfrentar situações atípicas decorrentes dos índices pretendidos. Podemos já vislumbrar o modo pelo qual a expansão dos mercados mundiais assume importantes posições no estabelecimento do processo de comunicação como um todo. <br />

          Gostaria de enfatizar que o julgamento imparcial das eventualidades garante a contribuição de um grupo importante na determinação do investimento em reciclagem técnica. Todavia, a contínua expansão de nossa atividade agrega valor ao estabelecimento da gestão inovadora da qual fazemos parte. Ainda assim, existem dúvidas a respeito de como a competitividade nas transações comerciais obstaculiza a apreciação da importância do remanejamento dos quadros funcionais. O empenho em analisar o início da atividade geral de formação de atitudes é uma das consequências dos relacionamentos verticais entre as hierarquias. Percebemos, cada vez mais, que o surgimento do comércio virtual pode nos levar a considerar a reestruturação dos procedimentos normalmente adotados. </p>
      </b-row>
      <div slot="footer">
        <ul>
          <li>
            <div class="text-muted">Visits</div>
            <strong>29.703 Users (40%)</strong>
            <b-progress
              height="{}"
              class="progress-xs mt-2"
              :precision="1"
              variant="success"
              :value="40"
            ></b-progress>
          </li>
          <li class="d-none d-md-table-cell">
            <div class="text-muted">Unique</div>
            <strong>24.093 Users (20%)</strong>
            <b-progress
              height="{}"
              class="progress-xs mt-2"
              :precision="1"
              variant="info"
              :value="20"
            ></b-progress>
          </li>
          <li>
            <div class="text-muted">Pageviews</div>
            <strong>78.706 Views (60%)</strong>
            <b-progress
              height="{}"
              class="progress-xs mt-2"
              :precision="1"
              variant="warning"
              :value="60"
            ></b-progress>
          </li>
          <li class="d-none d-md-table-cell">
            <div class="text-muted">New Users</div>
            <strong>22.123 Users (80%)</strong>
            <b-progress
              height="{}"
              class="progress-xs mt-2"
              :precision="1"
              variant="danger"
              :value="80"
            ></b-progress>
          </li>
          <li class="d-none d-md-table-cell">
            <div class="text-muted">Bounce Rate</div>
            <strong>40.15%</strong>
            <b-progress height="{}" class="progress-xs mt-2" :precision="1" :value="40"></b-progress>
          </li>
        </ul>
      </div>
    </b-card>
    <b-row>
      <b-col sm="6" lg="3">
        <div class="social-box facebook">
          <i class="fa fa-facebook"></i>
          <div class="chart-wrapper">
            <social-box-chart-example :data="[65, 59, 84, 84, 51, 55, 40]" height="90" />
          </div>
          <ul>
            <li>
              <strong>89k</strong>
              <span>friends</span>
            </li>
            <li>
              <strong>459</strong>
              <span>feeds</span>
            </li>
          </ul>
        </div>
        <!--/.social-box-->
      </b-col>
      <b-col sm="6" lg="3">
        <div class="social-box twitter">
          <i class="fa fa-twitter"></i>
          <div class="chart-wrapper">
            <social-box-chart-example :data="[1, 13, 9, 17, 34, 41, 38]" height="90" />
          </div>
          <ul>
            <li>
              <strong>973k</strong>
              <span>followers</span>
            </li>
            <li>
              <strong>1.792</strong>
              <span>tweets</span>
            </li>
          </ul>
        </div>
        <!--/.social-box-->
      </b-col>
      <b-col sm="6" lg="3">
        <div class="social-box linkedin">
          <i class="fa fa-linkedin"></i>
          <div class="chart-wrapper">
            <social-box-chart-example :data="[78, 81, 80, 45, 34, 12, 40]" height="90" />
          </div>
          <ul>
            <li>
              <strong>500+</strong>
              <span>contacts</span>
            </li>
            <li>
              <strong>292</strong>
              <span>feeds</span>
            </li>
          </ul>
        </div>
        <!--/.social-box-->
      </b-col>
      <b-col sm="6" lg="3">
        <div class="social-box google-plus">
          <i class="fa fa-google-plus"></i>
          <div class="chart-wrapper">
            <social-box-chart-example :data="[35, 23, 56, 22, 97, 23, 64]" height="90" />
          </div>
          <ul>
            <li>
              <strong>894</strong>
              <span>followers</span>
            </li>
            <li>
              <strong>92</strong>
              <span>circles</span>
            </li>
          </ul>
        </div>
        <!--/.social-box-->
      </b-col>
    </b-row>

    <b-row>
      <b-col md="12">
        <b-card header="Notícias">
          <b-table
            class="mb-0 table-outline"
            responsive="sm"
            hover
            :items="tableItems"
            :fields="tableFields"
            head-variant="light"
          ></b-table>
        </b-card>
      </b-col>
    </b-row>
   </div>
</template>

<script>
import CardLine1ChartExample from "~/components/dashboard/CardLine1ChartExample";
import CardLine2ChartExample from "~/components/dashboard/CardLine2ChartExample";
import CardLine3ChartExample from "~/components/dashboard/CardLine3ChartExample";
import CardBarChartExample from "~/components/dashboard/CardBarChartExample";
import MainChartExample from "~/components/dashboard/MainChartExample";
import SocialBoxChartExample from "~/components/dashboard/SocialBoxChartExample";
import CalloutChartExample from "~/components/dashboard/CalloutChartExample";
import { Callout } from "~/components/";
import { mapGetters } from "vuex";
import axios from "axios";

export default {
  name: 'dashboard',
  layout: 'menu/petiano',
  components: {
    Callout,
    CardLine1ChartExample,
    CardLine2ChartExample,
    CardLine3ChartExample,
    CardBarChartExample,
    MainChartExample,
    SocialBoxChartExample,
    CalloutChartExample
  },
  data: function() {
    return {
      noticia: {
        titulo: "",
        corpo: "",
        data_inicio: "",
        data_fim: ""
      },
      selected: "Month",
      tableItems: null,
      tableFields: {
        avatar: {
          label: '<i class="icon-people"></i>',
          class: "text-center"
        },
        user: {
          label: "User"
        },
        country: {
          label: "Country",
          class: "text-center"
        },
        usage: {
          label: "Usage"
        },
        payment: {
          label: "Payment method",
          class: "text-center"
        },
        activity: {
          label: "Activity"
        }
      }
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
        .get("http://epet.imd.ufrn.br/service/api/noticia", {
          auth: { username: "teste@gmail.com", password: "123456789" }
        })
        .then(res => {
          let result = res.data.content;
          let itens = [];
          let e = null;
          for (e of result) {
            itens.push({
              titulo: e.titulo,
              texto: e.corpo
            });
          }
          this.tableItems = itens;
          console.log(itens);
        });
    },

    variant(value) {
      let $variant;
      if (value <= 25) {
        $variant = "info";
      } else if (value > 25 && value <= 50) {
        $variant = "success";
      } else if (value > 50 && value <= 75) {
        $variant = "warning";
      } else if (value > 75 && value <= 100) {
        $variant = "danger";
      }
      return $variant;
    },
    flag(value) {
      return "flag-icon flag-icon-" + value;
    }
  }
};
</script>