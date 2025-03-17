<template>
    <div class="container"> <!-- Encapsule todo o conteúdo aqui -->
      <h1>Comentários</h1>
      <hr />
      <FormToDo v-on:add-todo="addComment"/>
      <div class="list-group"> 
        <p v-if="comments.length <= 0">Sem Comentários...</p>
        <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
          <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
          <p>
            mensagem: <strong>{{ comment.message }}</strong>
          </p>
          <div>
            <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
          </div>
        </div>
      </div>
      <hr />
    </div>
</template>
  

<script>
import FormToDo from './FormToDo.vue';

export default {
  components: {
    FormToDo
  },
  data() {
    return {
      comments: [],
      name: '',
      message: ''                
    }
  },

  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },

  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  },

  watch: {
    comments(val) {
      console.log('Comentários atualizados!', val);
    }
  }
}
</script>
