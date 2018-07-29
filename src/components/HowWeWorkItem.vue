<template>
    <div class="how_we_work_item">
        <img
            :src="require('../assets/in-description-arrow.png')"
            v-if="!is_last"
            class="how_we_work_arrow"
        />
        <div class="how_we_work_item_flex">
            <img :src="iconSrc" />
            <p v-html="description" class="clickable"></p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'how-we-work-item',

        props: {
            icon: {
                type: String,
                required: true
            },
            description: {
                type: String,
                required: true
            },
            is_last: {
                type: Boolean,
                required: true,
                default: false
            }
        },

        computed: {

            iconSrc() {
                return require('../assets/' + this.icon);
            }

        }
    }
</script>