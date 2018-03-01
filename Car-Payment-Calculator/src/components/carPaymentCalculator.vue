<template>
    <div class="calculator">
        <h1>Car Payment Calculator</h1>
        <hr>
        <h5>Loan Amount: ($)</h5>
        <input v-model="loanAmount">
        <hr>
        <h5>Interest Rate: (%)</h5>
        <input v-model="interestRate">
        <hr>
        <h5>Months:</h5>
        <input v-model="months">
        <hr>
        <h5>Downpayment: ($)</h5>
        <input v-model="downPayment">
        <hr>
        <br>
        <h3 class="align-text--right">Monthly Payment: ${{ monthlyPayment }}</h3>
    </div>
</template>

<script>
    module.exports= {
        name: "carPaymentCalculator",
        data() {
            return {
                loanAmount: 12000,
                months: 48,
                interestRate: 3.6, //Percentage
                downPayment: 2500
            }
        },
        computed: {
            monthlyPayment: function() {
                let amount = parseInt(this.loanAmount);
                let months = parseInt(this.months);
                let down = parseInt(this.downPayment);
                let annualInterest = parseInt(this.interestRate);
                let monthlyInterest = annualInterest / 1200;

                return ((monthlyInterest + (monthlyInterest / (Math.pow((1 + monthlyInterest), months) -1))) * (amount - (down || 0))).toFixed(2);
            }
        }
    }
</script>

<style>
    .calculator {
        padding: 2rem;
        border: 1px solid black;
    }
    .align-text--right {
        text-align: right;
    }
    input {
        margin-bottom: 1rem;
    }
    h5 {
        margin-top: 1rem;
        margin-bottom: 0.5rem;
    }
</style>
