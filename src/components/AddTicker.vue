<template>
    <section>
        <div class="flex">
            <div class="max-w-xs">
                <label for="wallet" class="block text-sm font-medium text-gray-700">Ticker</label>
                <div class="mt-1 relative rounded-md shadow-md">

                    <input v-model="ticker" @keydown.enter="add" type="text" name="wallet" id="wallet"
                        class="block w-full pr-10 border-gray-300 text-gray-900 focus:outline-none focus:ring-gray-500 focus:border-gray-500 sm:text-sm rounded-md"
                        placeholder="For example DOGE"
                        style="text-transform: uppercase;" />
                </div>
            </div>
        </div>

        <AddButton @click="add" type="button" :disabled="disabled"
            class="my-4 inline-flex items-center py-2 px-4 border border-transparent shadow-sm text-sm leading-4 font-medium rounded-full text-white bg-gray-600 hover:bg-gray-700 transition-colors duration-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500" />
    </section>
</template>
<script>
import AddButton from './AddButton.vue';

export default {
    components: {
        AddButton
    },

    props: {
        disabled: {
            type: Boolean,
            required: false,
            default: false
        }
    },

    emits: {
        "add-tickers": value => typeof value === "string" && value.length > 0
    },

    data() {
        return { ticker: "" }
    },
    methods: {
        add() {
            if (this.ticker.length === 0) {
                return
            }
       
            this.$emit("add-ticker", this.ticker)
            this.ticker = "";

        },
    }
}

</script>
