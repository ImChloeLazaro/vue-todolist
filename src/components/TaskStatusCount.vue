<script>
export default {
    props: {
        status: {
            type: String,
            required: true
        },
        count: {
            type: Number,
            required: true
        }
    }
}
</script>
<template>
    <span class="badge rounded-pill" :class="{
        'bg-primary': status === 'todo',
        'bg-success': status === 'done',
    }">
        {{ status }} 
        <span class="badge" :class="{
            'bg-primary': status === 'todo',
            'bg-success': status === 'done',
        }">
            {{ count }}
        </span>
    </span>
</template>