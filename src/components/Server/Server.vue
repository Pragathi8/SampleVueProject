<template>
    <li
        class="list-group-item"
        @click="showDetails">
        Server #{{ server.id }}
    </li>
</template>

<script>
import {eventBus} from '../../main';

export default {
    props: {
        "server": {
            type: Object
        }
    },
    methods: {
        showDetails() {
            eventBus.$emit('serverWasSelected', this.server);
        }
    }
}
</script>

<style scoped>
    .list-group-item {
        cursor: pointer;
        box-shadow: 1px 1px 1px #3434;
        margin: 2px;
    }
</style>