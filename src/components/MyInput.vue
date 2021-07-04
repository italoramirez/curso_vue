<template>
    <div class="input-wrapper">
        <div class="labels">
            <label :for="name"> {{ name }} </label>
            <div class="error">{{ error }}</div>
        </div>
        <input :id="name" type="text" :value="value" @input="input">
    </div>
</template>

<script>
    export default {
        name: 'MyInput',
        props: {
            name: {
                type: String,
                required: false
            },
            rules: {
                type: Object
            },
            value: {
                type: String
            }
        },
        
        computed: {
            error () {
                if ( this.rules.required && !this.value.length === 0 ) {
                    return 'Requerido';
                } else if ( this.rules.min && this.value.length < this.rules.min) {
                    return `Debe ingresar mínimo ${this.rules.min}`;
                }
                return '';
            }
        },
        methods: {
            input ( $evt ) {
                this.$emit('update', { 
                    $value: $evt.target.value,
                    name  : this.name 
                });
            }
        }

        
    }
</script>

<style scoped>
    .input-wrapper {
        display: flex;
        flex-direction: column;
    }

    .error {
        color: red;
    }
    .labels {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    input {
        background: none;
        color: #000000;
        border: 1px solid silver ;
        border-radius: 5px;
        padding: 10px;
        font-size: 16px;
        margin: 5px 0;
    }
</style>