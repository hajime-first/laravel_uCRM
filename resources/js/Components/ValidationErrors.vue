<script setup>
import { computed } from 'vue';

const props = defineProps({
    errors: Object
})

const hasErrors = computed(() => {
    if (props.errors && typeof props.errors === 'object') {
        return Object.keys(props.errors).length > 0;
    }
    return false;
});
</script>

<template>
    <div v-if="hasErrors">
        <div class="font-medium text-red-600">問題が発生しました。</div>

        <ul class="mt-3 list-disc list-inside text-sm text-red-600">
            <li v-for="(error, key) in props.errors" :key="key">{{ error }}</li>
        </ul>
    </div>
</template>