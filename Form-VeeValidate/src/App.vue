<template>
    <div id="app">
        <form @submit.prevent="handleSubmit">
            <!-- Name -->
            <div class="field">
                <label class="label">Name</label>
                <p class="control has-icon has-icon-right">
                    <input name="name" v-model="name" data-vv-delay="500" v-validate="'required|alpha'" :class="{'input': true, 'has-error': errors.has('name') }" type="text" placeholder="Name">
                    <i v-show="errors.has('name')" class="fa fa-warning"></i>
                    <span v-show="errors.has('name')" class="help has-error">{{ errors.first('name') }}</span>
                </p>
            </div>
            <!-- /Name -->
            <!-- Email -->
            <div class="field">
                <label class="label">Email</label>
                <p class="control has-icon has-icon-right">
                    <input name="email" v-model="email" data-vv-delay="500" v-validate="'required|email'" :class="{'input': true, 'has-error': errors.has('email') }" type="text" placeholder="Email">
                    <i v-show="errors.has('email')" class="fa fa-warning"></i>
                    <span v-show="errors.has('email')" class="help has-error">{{ errors.first('email') }}</span>
                </p>
            </div>
            <!-- /Email -->
            <!-- Phone -->
            <div class="field">
                <label class="label">Phone</label>
                <p class="control has-icon has-icon-right">
                    <input name="phone" v-model="phone" data-vv-delay="500" v-validate="'required|numeric'" :class="{'input': true, 'has-error': errors.has('phone') }" type="text" placeholder="Phone">
                    <i v-show="errors.has('phone')" class="fa fa-warning"></i>
                    <span v-show="errors.has('phone')" class="help has-error">{{ errors.first('phone') }}</span>
                </p>
            </div>
            <!-- /Phone -->
            <!-- URL -->
            <div class="field">
                <label class="label">Website</label>
                <p class="control has-icon has-icon-right">
                    <input name="url" v-model="url" data-vv-delay="500" v-validate="'required|url'" :class="{'input': true, 'has-error': errors.has('url') }" type="text" placeholder="Website">
                    <i v-show="errors.has('url')" class="fa fa-warning"></i>
                    <span v-show="errors.has('url')" class="help has-error">{{ errors.first('url') }}</span>
                </p>
            </div>
            <!-- /URL -->
            <!-- Submit -->
            <div class="column is-12">
                <p class="control">
                    <button class="button is-primary" type="submit">Submit</button>
                </p>
            </div>
            <!-- /Submit -->
        </form>
    </div>
</template>

<script>
export default {
    name: 'app',
    data: () => ({
        email: '',
        name: '',
        phone: '',
        url: ''
    }),
    methods: {
        handleSubmit() {
            this.$validator.validateAll().then((result) => {
                if (result) {
                    // Send data to server
                    alert('Form Submitted!');
                    return;
                }
                alert('Correct the errors!');
            });
        }
    }
};
</script>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    height: 100vh;
    display: flex;
    flex-direction: column;
    padding: 4rem;
}

form {
    margin: 0 auto;
    min-width: 400px;
}

.field {
    padding: 0.5rem 0;
}

input {
    display: block;
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #dbdbdb;
    border-radius: 3px;
}

input + span.help {
    display: block;
}

input.has-error {
    border: 1px solid hsl(348, 100%, 61%);
}

.control {
    margin-top: 0.5rem;
}

.control > span.help {
    padding: 1rem 0;
    color: hsl(348, 100%, 61%);
    font-size: 0.8rem;
}

label {
    color: #363636;
    display: block;
    font-size: 1rem;
    font-weight: 700;
}

.button {
    -moz-appearance: none;
    -webkit-appearance: none;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    border: 1px solid transparent;
    border-radius: 3px;
    -webkit-box-shadow: none;
    box-shadow: none;
    display: -webkit-inline-box;
    display: -ms-inline-flexbox;
    display: inline-flex;
    font-size: 1rem;
    height: 2.25em;
    -webkit-box-pack: start;
    -ms-flex-pack: start;
    justify-content: flex-start;
    line-height: 1.5;
    padding-bottom: calc(0.375em - 1px);
    padding-left: calc(0.625em - 1px);
    padding-right: calc(0.625em - 1px);
    padding-top: calc(0.375em - 1px);
    position: relative;
    vertical-align: top;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    background-color: white;
    border-color: #dbdbdb;
    color: #363636;
    cursor: pointer;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    justify-content: center;
    padding-left: 0.75em;
    padding-right: 0.75em;
    text-align: center;
    white-space: nowrap;
}

button.is-primary {
    background-color: #00d1b2;
    border-color: transparent;
    color: #fff;
}

</style>
