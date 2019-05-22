<template>
    <div class="node-column line__top">
        <div v-if="node.id != 0" class="line"></div>
        <div
            class="node"
            :class="{ 'active':node.employees }"
            @click="showMoreToggle"
        >

            <!------------>
            <!-- HEADER -->
            <!------------>
            <div class="node__header">
                {{ node.id }} - {{ node.team }}
            </div>

            <!----------->
            <!-- TITLE -->
            <!----------->
            <div class="node__title">
                <div class="node__title--name">
                    {{ node.name }} {{ node.id }}
                </div>
                <div class="node__title--position">
                    {{ node.designation }}
                </div>
            </div>

            <!------------->
            <!-- CONTENT -->
            <!------------->
            <div class="node__content">
                <div class="content1" title="Total number of direct employees">
                    <div class="icon-square">
                        <i class="fa fa-sitemap"></i>
                    </div>
                    <div v-if="node.employees">
                        {{ node.employees.length }}
                    </div>
                    <div v-else>0</div>
                </div>
                <div class="content2" title="Total number of employees">
                    <div class="icon-square">
                        <i class="fa fa-user"></i>
                    </div>
                    <div v-if="totalEmployees">
                        {{ totalEmployees }}
                    </div>
                    <div v-else>0</div>
                </div>
                <div class="content3" title="Total number of employees that have more employees">
                    <div class="icon-square">
                        <i class="fa fa-plus-circle"></i>
                    </div>
                    <div v-if="hasEmployees">
                        {{ hasEmployees }}
                    </div>
                    <div v-else>0</div>
                </div>
            </div>

            <!------------>
            <!-- FOOTER -->
            <!------------>
            <div class="node__footer">
                <div class="footer1 icon-square" title="Add an employee">
                    <i class="fa fa-user-plus"></i>
                </div>
                <div class="footer2 icon-square" title="Edit">
                    <i class="fa fa-pencil-alt"></i>
                </div>
                <div class="footer3 icon-square" title="Delete this employee">
                    <i class="fa fa-trash"></i>
                </div>
            </div>
        </div>

        <!-------------------->
        <!-- NODE INCEPTION -->
        <!-------------------->
        <transition name="fade">
            <div class="node-row" v-if="node.employees && showMore">
                <div class="line"></div>
                <div class="node-tree__inception">
                    <node v-for="employee in node.employees.slice(0, 4)" :node="employee"></node>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
    export default {
        name: "node",
        props: {
            node: Object,
            default: null,
        },
        data () {
            return {
                showMore: false,
            }
        },
        methods: {
            /**
             * TOGGLE
             */
            showMoreToggle () {
                this.showMore = !this.showMore;
            }
        },
        computed: {
            /**
             * TOTAL NUMBER OF EMPLOYEES UNDER
             * @returns {boolean|number}
             */
            totalEmployees () {
                if (!this.node.employees) {
                    return false;
                }
                var sum = 0;
                this.node.employees.forEach(e => {
                    sum += e.length;
                });
                return sum;
            },

            /**
             * NUMBER OF EMPLOYEES DIRECTLY UNDER
             * @returns {boolean|*}
             */
            hasEmployees () {
                if (!this.node.employees) {
                    return false;
                }
                return this.node.employees.filter(value => value.employees).length;
            }
        }
    };
</script>

<style lang="scss" scoped>

    //SIZES
    $info-height: 2.5em;
    $line-width: .25em;
    $line-height: 9.375em;
    $node-width: 25em;
    $node-limit: 4;
    $node-max: ($node-width * $node-limit);
    $icon-square: 2.5em;

    //COLORS
    $color-border: #ddd;
    $color-bg: #f6f6f6;
    $color-icon: #408FBA;

    //SHADOWS
    $shadow-1: #{0 .25em .5em -.25em rgba(0, 0, 0, .3)};
    $shadow-2: #{0 .125em .5em rgba(0,0,0,.3)};
    
    //ANIMATIONS
    $transition-delay: 150ms;
    $transition: all $transition-delay ease-in-out;




    //*** NODE ***/
    .node {
        //*** EACH NODE ***/
        width: $node-width;
        background:$color-bg;
        border:1px solid $color-border;
        margin: 0 auto;
        box-shadow: $shadow-1;
        line-height: 1.5em;

        //*** HEADER ***/
        &__header {
            background: white;
            border-bottom: 1px solid $color-border;
            min-height: $info-height;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: .5em;
            font-size: 1.25em;
        }

        //*** TITLE ***/
        &__title {
            background: white;
            min-height: $info-height;
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

            .fa {
                color: $color-icon;
            }
            .footer1 .fa {
                color: limegreen;
            }
            .footer2 .fa {
                color: black;
            }
            .footer3 .fa {
                color: red;
            }
        }

        //*** NODE ACTIVE STATUS STYLES ***/
        &.active {
            cursor: pointer;
            transition: $transition;
            &:hover {
                box-shadow: $shadow-2;
                transition: $transition;
            }
            & .node__header {
                background: teal;
                color: white;
            }
        }

        //*** TREE GRID ***/
        &-column {
            &.line__top {
                &:not(:only-child):before {
                    content: '';
                    display: block;
                    position: relative;
                    width: 100%;
                    height: $line-width;
                    background: $color-border;
                }

                &:first-child {
                    &:before {
                        left: 50%;
                    }
                }

                &:last-child {
                    &:before {
                        left: calc(-50% + #{$line-width});
                    }
                }
            }
        }
        &-row {
            max-width: $node-max;
            margin: 0 auto;
        }
        &-tree__inception {
            display: flex;
            justify-content: space-between;
        }
    }




    //*** LINE ***/
    .line {
        height: $line-height;
        width: $line-width;
        background: $color-border;
        display:block;
        position:relative;
        bottom: 0;
        left: 50%;
    }



    //*** ICONS ***/
    .icon-square {
        display: flex;
        align-items: center;
        justify-content: center;
        min-width: $icon-square;
        min-height: $icon-square;
        transition: $transition;
        &:hover {
            background: $color-bg;
            transition: $transition;
        }
    }



    //*** STANDARD FADE ***/
    // <transition name="fade">
    .fade {
        &-enter-active,
        &-leave-active {
            transition: opacity $transition-delay ease-in-out;
            will-change: opacity;
        }

        &-enter-active {
            transition-delay: $transition-delay;
        }

        &-enter,
        &-leave-active {
            opacity: 0;
        }
    }
</style>