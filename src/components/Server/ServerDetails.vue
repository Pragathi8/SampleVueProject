<template>
    <div class="col-xs-12 col-sm-6 serverDetails">
        <p v-if="!server">Server Details are currently not updated</p>
        <div v-else>
            <p>Server #{{server.id}} selected, Status: {{server.status}}</p>
            <hr>
            <button @click="switchServerStatus">Set Status to OK</button>
        </div>

    </div>

</template>

<script>
    import {eventBus} from '../../main';
    export default {
        data: function() {
            return {
                server: null
            }
        },
        methods: {
            switchServerStatus() {
                this.server.status = "OK";
            }
        },
        created() {
            eventBus.$on('serverWasSelected', (data) => {
                this.server = data;
            })
        }
    }
</script>

<style>
    .serverDetails {
        box-shadow: 2px 2px 2px 2px #3434;
        padding: 10px;
    }
</style>
