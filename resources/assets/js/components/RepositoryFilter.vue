<template>
    <div>
        <div class="flex">
            <input
                class="flex-auto shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
                placeholder="Looking for something?"
                v-model="_filterRepositories"
            >

            <button
                v-if="_filterRepositories"
                @click="__clearFilter()"
                class="flex-1 bg-red ml-2 hover:bg-red-dark text-white font-bold py-2 px-4 rounded"
                type="button"
            >
                <i class="fas fa-trash"></i>
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['repository'],

        computed: {
            _filterRepositories: {
                get() {
                    return this.$store.state.home.data.filterRepositories
                },
                set(value) {
                    this.$store.commit('homeSetFilterRepositories', value)
                }
            }
        },

        methods: {
            __formatNumber(number) {
                return number.toLocaleString()
            },

            __keywords(repository) {
                return repository.keywords
            },

            __clearFilter() {
                return this.$store.commit('homeSetFilterRepositories', '')
            },
        },
    }
</script>

