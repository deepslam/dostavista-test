<template>
    <div id="how_we_work">
        <h3 class="clickable">{{title}}</h3>
        <div id="how_we_work_container">
            <slot/>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'how-we-work',

        props: {
            title: {
                type: String,
                required: true
            }
        }
    }
</script>