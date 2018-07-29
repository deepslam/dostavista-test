<template>
  <div id="container">
    <header-main/>
    <header-description-block/>
    <content-main
      heading="Почему Достависта?"
    >
      <div id="why_dostavista_container" class="border_bottom">
        <why-dostavista
                v-for="(whyBlock,key) in whyBlocksItems"
                :key="key"
                :title="whyBlock.title"
                :description="whyBlock.description"
                :is_last="key == (whyBlocksLength - 1)"
        />
      </div>
      <how-we-work title="Как мы работаем?">
        <how-we-work-item
                v-for="(howWeWork,key) in howWeWorkItems"
                :key="key"
                :icon="howWeWork.icon"
                :description="howWeWork.description"
                :is_last="key == (howWeWorkItemsLength - 1)"
        />
      </how-we-work>
    </content-main>
  </div>
</template>

<script>
import jQuery from 'jquery';

import HeaderMain from './components/HeaderMain';
import HeaderDescriptionBlock from './components/HeaderDescriptionBlock.vue';
import ContentMain from './components/ContentMain.vue';
import WhyDostavista from './components/WhyDostavista.vue';
import HowWeWork from './components/HowWeWork.vue';
import HowWeWorkItem from './components/HowWeWorkItem.vue';

import DostavistaItems from './config/why_blocks.json';
import HowWeWorkItems from './config/how_we_work.json';

export default {
    name: 'app',

    components: {
        HowWeWorkItem,
        HeaderMain,
        HeaderDescriptionBlock,
        ContentMain,
        WhyDostavista,
        HowWeWork
    },

    computed: {

        whyBlocksItems() {
          if (
              typeof DostavistaItems == "object" &&
              typeof DostavistaItems.items != "undefined" &&
              Array.isArray(DostavistaItems.items)
          ) {
              return DostavistaItems.items;
          } else {
              return [];
          }
        },
        whyBlocksLength() {
            return this.whyBlocksItems.length;
        },

        howWeWorkItems() {
            if (
                typeof HowWeWorkItems == "object" &&
                typeof HowWeWorkItems.items != "undefined" &&
                Array.isArray(HowWeWorkItems.items)
            ) {
                return HowWeWorkItems.items;
            } else {
                return [];
            }
        },
        howWeWorkItemsLength() {
            return this.howWeWorkItems.length;
        }

    },

    mounted() {
        jQuery(document).ready(function() {
            jQuery(".clickable").click(function(e) {
                let s = window.getSelection();
                let range = s.getRangeAt(0);
                let node = s.anchorNode;
                while (range.toString().indexOf(' ') != 0 && range.startOffset > 0) {
                    let newOffset = range.startOffset - 1;
                    if (newOffset < 0) {
                        newOffset = 0;
                    }
                    range.setStart(node, newOffset);
                }
                if (range.startOffset > 0) {
                    range.setStart(node, range.startOffset + 1);
                }
                do {
                    range.setEnd(node, range.endOffset + 1);
                } while (range.toString().indexOf(' ') == -1 && range.toString().trim() != '' && range.endOffset < node.length);

                const offset = range.endOffset;
                node.nodeValue = node.nodeValue.substring(0, range.startOffset) + '' + node.nodeValue.substring(offset, node.length);
            });
        });
    }
}
</script>