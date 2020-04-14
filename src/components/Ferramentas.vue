<template>
  <div id="ferramentas">
      <select v-model="caixaSel">
          <option value="" selected disabled>Selecione uma caixa</option>
          <option v-for="(caixa, index) in caixinhas" :key="index" :value="index">
              {{ caixa.titulo }}
          </option>
      </select>
  <div id="paleta">
      <div class="corr" :style="cor" v-for="(cor, index) in cores" :key="index" @click="alteraCor(cor)"></div>
        </div>
        <input type="text" placeholder="digite o nome da caixa" v-model="titulo">
        <button @click="alterarTexto" >OK</button>
  </div>
</template>

<script>
export default {
    name: "Ferramentas",
    computed:{
        caixinhas(){
            return this.$store.state.caixinhas
         }
    },
    data: function(){
        return{
            cores: ['background: brown', 'background: white', 'background: green'],
            caixaSel: '',
            titulo: ''
        }
    }, methods:{
        alteraCor: function(cor){
            this.$store.commit('alteraCor', {
                cor: cor,
                caixa: this.caixaSel
            })
        },
        alterarTexto: function(){
            this.$store.commit('alterouTexto',{
                titulo: this.titulo,
                caixa: this.caixaSel
            })
        }
    }
}
</script>

<style>
    #ferramentas{
        width: 380px;
        height: 150px;
        border: 1px solid white;
        margin: 5px auto 0px auto;
        padding: 20px;
    }
    #ferramentas select{
        margin-bottom: 5px;
        width: 360px;
    }
    #paleta{
        display: flex;
        width: 380px;
        height: 130px;
    }
    .corr{
        width: 60px;
        height: 60px;
        margin-right: 3px;
        border: 1px solid white;
    }
</style>