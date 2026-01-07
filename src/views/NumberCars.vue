<script setup>
import { ref } from 'vue';

const arrStr = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'];
const arrNum = [0,1,2,3,4,5,6,7,8,9];
const allCars = ref('')
const countCars = ref(0);
let intervalId = null;
// NUMBERS
const one = ref('A')
const two = ref(0)
const three = ref(0)
const four = ref(0)
const five = ref('A')
const six = ref('A')
const start = () => {
    intervalId = setInterval(() => {
        if (six.value !== "Z") {
            six.value = six.value ? SearchIndex(six.value, 'str') : 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else if (five.value !== "Z") {
            five.value = five.value ? SearchIndex(five.value, 'str') : 'A';
            six.value = 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else if (four.value !== 9) {
            four.value = four.value ? SearchIndex(four.value, 'num') : 1;
            five.value = "A";
            six.value = 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else if (three.value !== 9) {
            three.value = three.value ? SearchIndex(three.value, 'num') : 1;
            four.value = 0;
            five.value = 'A';
            six.value = 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else if (two.value !== 9) {
            two.value = two.value ? SearchIndex(two.value, 'num') : 1;
            three.value = 0;
            four.value = 0;
            five.value = 'A';
            six.value = 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else if (one.value !== "Z") {
            one.value = one.value ? SearchIndex(one.value, 'str') : 'A';
            two.value = 0;
            three.value = 0;
            four.value = 0;
            five.value = 'A';
            six.value = 'A';
            allCars.value = `${one.value}${two.value}${three.value}${four.value}${five.value}${six.value}`;
            countCars.value += 1;
        } else {
            clearInterval(intervalId);
        }

    }, 1);
};

const SearchIndex = (txt, type) => {

    if (type === 'str') {
        const idx = arrStr.indexOf(txt)
        const result = arrStr[idx + 1];
        if (result) return result;
        return txt;
    } else if (type === 'num') {
        const idx = arrNum.indexOf(txt)
        const result = arrNum[idx + 1];
        if (result === undefined || result === null) return txt;
        return result;
    }
}

</script>
<template>
    <div class="w-[800px] gap-4 m-auto bg-gray-800 mt-80 p-8 flex items-center justify-center">
        <h1 class="text-center">{{ allCars }} ({{ countCars }})</h1>
        <Button 
            label="start"
            severity="info"
            @click="start"
        />
    </div>
</template>
<style scoped>
    
</style>