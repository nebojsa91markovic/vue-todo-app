<template>
    <div>
        <button :class="{ active: filter == 'all' }"
        @click="changedFilter('all')">
            All
        </button>
        <button :class="{ active: filter == 'active' }"
        @click="changedFilter('active')">
            Active
        </button>
        <button :class="{ active: filter == 'completed' }"
        @click="changedFilter('completed')">
            Completed
        </button>
    </div>
</template>

<script>
export default {
    name: 'TodoFiltered',
    computed: {
        filter() {
            return this.$store.state.filter
        }
    },
    methods: {
        changedFilter(filter) {
            this.$store.dispatch('updateFilter', filter);
        }
    }
}
</script>