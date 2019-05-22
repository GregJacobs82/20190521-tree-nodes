<template>
    <div class="tree">
        <div class="tree-list">
            <TreeList :node="collection"/>
        </div>
    </div>
</template>

<script>
    import TreeList from "./TreeList.vue";

    export default {
        components: {
            TreeList
        },
        props: {
            collection: Object,
            default: null
        },
    };
</script>