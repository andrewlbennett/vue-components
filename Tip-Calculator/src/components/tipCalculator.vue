<template>
    <div class="tip-calculator">
        <h1>Tip Calculator</h1>
        <hr>
        <ul>
            <li v-for="item in items">
                <p>{{item.name}}</p>
                <p>${{item.price}}</p>
            </li>
        </ul>
        <hr>
        <p>Items Total: ${{ getItemsListTotal }}</p>
        <p>Sales Tax: {{ getSalesTax }}%</p>
        <p>Subtotal: ${{ getSubTotal }}</p>
        <hr>
        <p><b>15%:</b> ${{ getSubTotal | tip15 }} = ${{ getTipTotal15 }}</p>
        <p><b>20%:</b> ${{ getSubTotal | tip20 }} = ${{ getTipTotal20 }}</p>
        <p><b>25%:</b> ${{ getSubTotal | tip25 }} = ${{ getTipTotal25 }}</p>
    </div>
</template>

<script>
    module.exports= {
        name: "tipCalculator",
        data() {
            return {
                items: [
                    {name:'chesseburger', price: 12.67},
                    {name:'fries', price: 5.34},
                    {name:'drink', price: 1.58},
                    {name:'cheesecake', price: 4.99}
                ],
                salesTaxPerc: .025 // Sales Tax Percentage
            }
        },
        computed: {
            getItemsListTotal: function() {
                var total = this.items.reduce(function(acc, items) {
                    return acc + Number(items.price);
                }, 0);
                return total.toFixed(2);
            },
            getSubTotal: function() {
                let total = this.items.reduce(function(acc, items) {
                    return acc + Number(items.price);
                }, 0);
                let taxIncluded = ((total * this.salesTaxPerc) + total).toFixed(2);
                return taxIncluded;
            },
            getSalesTax: function() {
                return (this.salesTaxPerc * 100).toFixed(1);
            },
            getTipTotal15: function() {
                let subTotal = this.getSubTotal;
                let tipTotal = (this.getSubTotal * .15);
                let total = (Number(tipTotal) + Number(subTotal)).toFixed(2);
                return total;
            },
            getTipTotal20: function() {
                let subTotal = this.getSubTotal;
                let tipTotal = (this.getSubTotal * .2);
                let total = (Number(tipTotal) + Number(subTotal)).toFixed(2);
                return total;
            },
            getTipTotal25: function() {
                let subTotal = this.getSubTotal;
                let tipTotal = (this.getSubTotal * .25);
                let total = (Number(tipTotal) + Number(subTotal)).toFixed(2);
                return total;
            }
        },
        filters: {
            tip15(value) {
                return (value * .15).toFixed(2);
            },
            tip20(value) {
                return (value * .2).toFixed(2);
            },
            tip25(value) {
                return (value * .25).toFixed(2);
            }
        }
    }
</script>

<style>

    .tip-calculator {
        padding: 2rem;
        border: 2px solid #2c3e50;
        min-width: 300px;
        border-radius: 4px;
        background-color: white;
    }

    li {
        display: flex;
        justify-content: space-between;
    }

    li + li {
        margin-top: 0.2rem;
    }

    li > p {
        margin: 0;
    }

</style>
