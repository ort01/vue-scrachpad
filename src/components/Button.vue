<script>
export default {
    name: "Button",
    props: {
        text: String,
        color: String
    }
}

</script>

<template>
    <button @click="$emit('btn-click')" :style="{ background: color }" class="btn">{{ text }}</button>
</template>




