<template>
    <div :class="classes">
        <div class="why_dostavista_item_title">
            <h3 class="clickable">{{title}}</h3>
        </div>
        <div class="why_dostavista_item_description">
            <p v-html="description" class="clickable"></p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'why-dostavista',

        props: {
            title: {
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

            classes() {
                const result = [];
                result.push('why_dostavista_item');
                if (!this.is_last) {
                    result.push('border_bottom');
                }
                return result;
            }

        }
    }
</script>