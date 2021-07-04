<template>
    <div>
        <button :style="{ background, color }" :disabled="disabled">
            Button
        </button>
    </div>
</template>

<script>
    export default {
        name: 'Button',
        props:  {
            color: {
                type: String
            },
            background: {
                type: String
            },
            disabled: {
                type: Boolean
            }
        }
       

    }
</script>

<style scoped>
    button:disabled {
        opacity: 0.5;
    }
    button {
        background: none;
        color: #000000;
        border: none;
        border-radius: 5px;
        padding: 10px 40px;
        font-size: 16px;
        cursor: pointer;
    }

    button:hover {
        filter: brightness(125%);
    }
</style>