<template>
    <div class="form-todo form-group">
        <p>
            <input type="text" placeholder="nome" name="author" class="form-control" v-model="name" />
        </p>
        <p>
            <textarea name="message" placeholder="Comentário" id="" class="form-control" v-model="message" ></textarea>
        </p>
        <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                message: ''
            }
        },
        methods: {
            addComment() {
                if (this.message === '') {         
                    alert('Por favor, preencha o campo de mensagem!'); 
                    return;
                }

                // Emitindo um evento para o componente pai
                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message
                });

                this.name = '';
                this.message = '';
            },
        }
    }
</script>