<template>
    <textarea class="autosize-textarea"
        :value="modelValue"
        rows="1"
        @input="$emit('update:modelValue', $event.target.value); resize()"/>
</template>

<script>
export default {
    name: 'AutosizeTextarea',

    props: {
        modelValue: {
            type: [String, null],
            required: true,
        },
    },

    emits: ['update:modelValue'],

    mounted() {
        this.$nextTick(this.resize);
    },

    methods: {
        resize() {
            this.$el.style.height = '1px';

            if (this.$el.scrollHeight > 0) {
                this.$el.style.height = `${this.$el.scrollHeight}px`;
            }
        },
    },
};
</script>

<style>
.autosize-textarea {
    overflow-y: hidden;
}
</style>