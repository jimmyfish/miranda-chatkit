<template>
    <div class="user-list">
        <h4>Members</h4>
        <hr>
        <b-list-group>
            <b-list-group-item v-for="user in users" :key="user.username">
                <span v-if="user.presence === 'online'" class="text-success">
                    ●
                </span>
                <span v-if="user.presence === 'offline'" class="text-danger">
                    ●
                </span>
                {{ user.username }}
            </b-list-group-item>
        </b-list-group>
    </div>
</template>

<script>
    import { mapState } from 'vuex'

    export default {
        name: 'user-list',
        computed: {
            ...mapState([
                'loading',
                'users'
            ])
        },
        methods: {
            statusColor(status) {
                return status === 'online' ? 'success' : 'warning'
            }
        }
    }
</script>