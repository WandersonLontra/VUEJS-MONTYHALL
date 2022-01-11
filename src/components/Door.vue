<template>

    <div class="door-area">
        <div class="door-frame" :class="{selected: isSelected && !isOpen}">
            <Gift  v-if="isOpen && hasGift"/>
        </div>
        <div class="door" :class="{open: isOpen}" @click="isSelected = !isSelected">
            <div class="number" :class="{selected: isSelected}">{{number}}</div>
            <div class="knob" 
                :class="{selected: isSelected}"
                @click.stop="isOpen = true"    
            ></div>
        </div>
    </div>

</template>

<script>
import Gift from './Gift.vue';

export default {
    name: 'Door',
    components: { Gift },
    props: {
        number: {},
        hasGift: { type: Boolean}
    },
    data(){
        return {
            isOpen: false,
            isSelected: false,
        }
    }
}
</script>

<style>
    :root{
        --door-border: 5px solid brown;
        --selected-border: 5px solid yellow;
    }

    .door-area{
        position: relative;
        width: 200px;
        height: 310px;
        border-bottom: 10px solid #aaa;
        margin-bottom: 20px;
        font-size: 3rem;

        display: flex;
        justify-content: center;
    }

    .door-frame{
        position: absolute;
        width: 180px;
        height: 300px;

        border-left: var(--door-border);
        border-top: var(--door-border);
        border-right: var(--door-border);

        display: flex;
        justify-content: center;
        align-items: center;
    }

    .door{
        position: absolute;
        top: 5px;
        height: 295px;
        width: 170px;
        background: chocolate;

        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
    }

    .door .knob{
        width: 20px;
        height: 20px;
        border-radius: 20px;
        background: brown;
        align-self: flex-start;
        margin-top: 60px;
    }

    .door-frame.selected{
        border-left: var(--selected-border);
        border-top: var(--selected-border);
        border-right: var(--selected-border);
    }

    .door .number.selected{
        color: yellow;
    }
    .door .knob.selected{
        background: yellow;
    }

    .door.open{
        background: #0007;
    }

    .door.open .knob{
        display: none;
    }

    .door.open .number{
        display: none;
    }
</style>