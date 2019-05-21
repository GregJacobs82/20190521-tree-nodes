<template>
    <div class="node active">
        <div class="node__header">
            {{ team }}
        </div>
        <div class="node__title">
            <div class="node__title--name">
                {{ name }} {{ id }}
            </div>
            <div class="node__title--position">
                {{ designation }}
            </div>
        </div>
        <div class="node__content">
            <div class="content1">
                <div>Immediate Employees</div>
                <div>{{ employees.length }}</div>
            </div>
            <div class="content2">
                Total Employees
            </div>
            <div class="content3">
                ( + )
            </div>
        </div>
        <div class="node__footer">
            <div class="footer1">
                [Add]
            </div>
            <div class="footer2">
                [Edit]
            </div>
            <div class="footer3">
                [Del]
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            id: {
                type: Number,
                default: null,
            },
            team: {
                type: String,
                required: true,
            },
            name: {
                type: String,
                required: true,
            },
            designation: {
                type: String,
                required: true,
            },
            employees: {
                type: Array,
                default() {
                    return [];
                },
            }
        },
    }
</script>

<style lang="scss" scoped>

    //SIZES
    $height: 40px;

    //COLORS
    $color-border: #ddd;
    $color-bg: #f6f6f6;

    //SHADOWS
    $shadow-1: #{0 4px 8px -4px rgba(0, 0, 0, .3)};
    $shadow-2: #{0px 2px 8px rgba(0,0,0,.3)};
    $shadow-3: #{0px 1px 2px rgba(0,0,0,.3)};
    $shadow-4: #{0 30px 50px -15px rgba(0,0,0,.35)};

    //*** NODE ***/
    .node {
        width: 400px;
        background:$color-bg;
        border:1px solid $color-border;
        margin: 0 auto;
        box-shadow: $shadow-1;
        line-height: 1.5em;

        //*** HEADER ***/
        &__header {
            background: white;
            min-height: $height;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: .5em;
            font-size: 1.25em;
        }

        //*** TITLE ***/
        &__title {
            background: white;
            min-height: $height;
            padding: 1em .5em;
            border-bottom: 1px solid $color-border;
            &--name {
                font-size: 1.25em;
            }
            &--position {
                color: #888;
            }
        }

        //*** CONTENT ***/
        &__content,
        &__footer {
            background: white;
            padding: 1em .5em;
            display: flex;
            align-items:center;
            justify-content: space-evenly;
                border-bottom: 1px solid $color-border;
        }

        //*** NODE ACTIVE STATUS STYLES ***/
        &.active {
            & .node__header {
                background: teal;
                color: white;
            }
        }
    }
</style>