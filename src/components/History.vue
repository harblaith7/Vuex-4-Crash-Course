<template>
    <div class="container">
        <h4> History </h4>
        <div class="flex">
            <p 
                v-for="(number, index) in history" 
                :key="index"
                :class="activeIndexes(parseInt(value)).includes(index) && 'bold'"
            >
                {{ number }}
            </p>
        </div>
        <input 
            placeholder="Search by Index" 
            type="number" 
            v-model="value"
        />
    </div>
</template>

<script>
import { mapState, mapGetters } from "vuex"

    export default {
        data() {
            return {
                value: 0
            }
        },
        computed: {
            ...mapState(["history"]),
            ...mapGetters(["activeIndexes"])
        }
    }
</script>

<style scoped>
    .container {
        margin-top: 7rem;
    }
    .flex {
        display: flex;
        text-align: center;
        width: 25rem;
        margin: 0 auto;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    .flex p {
        margin: 1rem
    }

    .bold {
        font-weight: 900;
    }
</style>