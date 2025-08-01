<script setup>
    const props = defineProps(['tarefas']);

    const temTarefaPendente = () => props.tarefas.length > 0 
</script>


<template>
    <ul v-if="temTarefaPendente()" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
            :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <span v-else class="message">Não há tarefas pendentes</span>
</template>

<style scoped>

    .done {
    color: orange;
    text-decoration: line-through;
    }

    .message {
        font-size: 4rem;
        font-style: italic;
    }
</style>