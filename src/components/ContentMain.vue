<template>
    <main class="content">
        <div class="heading border_bottom" v-if="heading != ''">
            <h1 class="clickable">{{heading}}</h1>
        </div>
        <div>
            <slot/>
        </div>
    </main>
</template>

<script>
    export default {
        name: 'content-main',

        props: {
            heading: {
                type: String
            }
        }
    }
</script>