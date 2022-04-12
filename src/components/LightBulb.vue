
<script>
export default {
    props: ["necessaryClicks"],
    emits: ["switchedOn"],
    data() {
        return {
            cargas: this.necessaryClicks
        }
    },
    methods: {
        decrementarCargas() {
            this.cargas--;

            // Cuando cargas == 0 -> hay que emitir un custom event que le hemos llamado 'switchedOn'. 
            if (this.cargas == 0) {
                // No hace falta pasar un parámetro porque tan solo nos queremos enterar que ya se ha encendido
                this.$emit('switchedOn');
            }
        }
    }

}
</script>

<template>
    <div v-if="cargas > 0" @click="decrementarCargas" class="bulb bulb-off">
        <p> {{ cargas }} </p>
    </div>
    <div v-else class="bulb bulb-on">
    </div>
</template>

<style scoped>
p {
    font-size: 1.5rem;
    font-weight: 700;
    transform: rotate(180deg);

}

.bulb {
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    user-select: none;
    transform: rotate(180deg);
}

.bulb-off {
    width: 265px;
    height: 400px;
    background: url('lightoff.png') no-repeat;
    margin: auto;
}

.bulb-on {
    width: 265px;
    height: 400px;
    background: url('lighton.png') no-repeat;
    ;
    margin: auto;
}
</style>