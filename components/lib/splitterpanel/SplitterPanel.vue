<template>
    <div ref="container" :class="cx('root')" v-bind="ptm('root', getPTOptions)">
        <slot></slot>
    </div>
</template>

<script>
import BaseSplitterPanel from './BaseSplitterPanel.vue';

export default {
    name: 'SplitterPanel',
    extends: BaseSplitterPanel,
    computed: {
        isNested() {
            return this.$slots.default().some((child) => {
                return child.type.name === 'Splitter';
            });
        },
        getPTOptions() {
            return {
                context: {
                    nested: this.isNested
                }
            };
        }
    }
};
</script>
