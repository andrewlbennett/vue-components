<template>
    <div class="tip-calculator">
        <h1>Tip Calculator</h1>
        <hr>
        <p>Subtotal: {{ subTotal }}</p>
        <p>Sales Tax: {{ salesTaxPerc }}%</p>
        <h3>Total:  ${{ subTotal | totalWithTax }}</h3>
        <hr>
        <p>15%: ${{ total | tip15 }} = ${{ total | tip15Total }}</p>
        <p>20%: ${{ total | tip20 }} = ${{ total | tip20Total }}</p>
        <p>25%: ${{ total | tip25 }} = ${{ total | tip25Total }}</p>
    </div>
</template>

<script>
    module.exports= {
        name: "tipCalculator",
        data() {
            return {
                subTotal: 65.43,
                total: 65.43,
                salesTaxPerc: 2.5 // Sales Tax Percentage
            }
        },
        filters: {
            totalWithTax(value) {
                return ((value * .025) + value).toFixed(2)
            },
            tip15(value) {
                return (value*.15).toFixed(2)
            },
            tip15Total(value) {
                return ((value*.15) + value).toFixed(2)
            },
            tip20(value) {
                return (value*.2).toFixed(2)
            },
            tip20Total(value) {
                return ((value*.2) + value).toFixed(2)
            },
            tip25(value) {
                return (value*.25).toFixed(2)
            },
            tip25Total(value) {
                return ((value*.25) + value).toFixed(2)
            }
        }
    }
</script>

<style>

    .tip-calculator {
        padding: 2rem;
        border: 1px solid black;
    }

</style>
