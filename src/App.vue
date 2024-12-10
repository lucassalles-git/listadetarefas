<script setup>
import { ref } from 'vue';
//variavel com tarefas
const tarefas = ref([
  'Concluir o curso Vai a Web',
  'Se preparar para a formatura',
  'Estudar vue.js',
  'Estudar React',
  'Estudar JavaScript'

])

function removerTarefa(index) {
  tarefas.value.splice(index, 1) // Remove 1 item da lista na posição 'index'
}

const novaTarefa = ref("")
//função de Add uma nova tarefas

function adicionarTarefa() {
  if (novaTarefa.value.trim() !== "") { //Verifica se o input não está vazio

    // !==: Verifica se os valores e os tipos são diferentes.
    tarefas.value.push(novaTarefa.value.trim()) // Adiciona a nova tarefa na lista
    novaTarefa.value = "" // Limpa o campo de texto
  }
}
</script>

<template>
  <main>

    <section class="list">

      <section class="title">
        <h1>📝 Lista de Tarefas</h1>
      </section>

      <section class="listas">

        <section class="add">

          <input type="text" placeholder="Digite sua nova tarefa" v-model="novaTarefa">

          <button @click="adicionarTarefa">Add</button>

        </section>


        <div v-if="tarefas.length === 0">
          <p class="felicitacao">🎉 Parabéns! Você completou todas as tarefas!</p>
        </div>
        <ul v-else>
          <li v-for="(tarefa, index) in tarefas" :key="index">{{ tarefa }}
            <button @click="removerTarefa(index)"> Finalizar</button>
          </li>
          <!-- v-for é um Loop. Estamos usando para renderizar cada elemento -->
          <!-- v-for="(item, posição do item) -->
          <!-- :key="index" para se necessário deletar a posição expecífica -->
        </ul>
      </section>

    </section>

  </main>

</template>

<style scoped lang="scss">
main {
  height: auto;

  display: flex;
  align-items: center;
  justify-content: center;

  .list {
    height: auto;
    width: 22vw;
    border: 15px solid #CD2F86;
    border-radius: 70px;
    box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.432);

    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #F3F0B9;

    font-family: "Roboto", sans-serif;
  }

  .title {
    width: 100%;
  }

  h1 {
    padding: 40px;
    border-radius: 55px 55px 0 0;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.116);
    background-color: #F4ABE2;
    font-size: 2.1rem;
    color: #FFFF;
    text-shadow: 1px 1px 10px rgba(0, 0, 0, 0.295);
  }

  .add {

    input {
      border: none;
      padding: 7px;
      height: 30px;
      width: 13vw;
      margin-right: 1vw;

      font-family: "Roboto", sans-serif;
      font-weight: 500;
      color: #a8276e;
    }

    button {
      padding: 7px;
      border: none;
      border-radius: 5px;
      background-color: #F4A773;
      font-family: "Roboto", sans-serif;
      font-weight: 500;
      color: #a8276e;
    }
  }

  .listas {
    height: auto;
    padding: 30px 20px;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 30px;
  }

  ul {
    height: auto;
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 30px;

    button {
      padding: 4px;
      border: none;
      background-color: #F4A773;
      font-family: "Roboto", sans-serif;
      font-weight: 500;
      color: #a8276e;
    }
  }

  li {
    padding: 5px;
    display: flex;
    justify-content: space-between;
    background-color: #F1DCA5;
    font-weight: 500;
    font-size: 1.05rem;
    color: #a8276e;
  }

  .felicitacao {
    font-family: "Roboto", sans-serif;
    font-weight: 500;
    font-size: 1.5em;
    text-align: center;
    color: #a8276e;
  }

  button, button:hover {
    background-color: #f1904e;
    transition: all 0.3s;
  }
}
</style>