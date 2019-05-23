<template>
    <div class="home" :style="{ fontSize: fontSize + 'px' }">
        <div class="flex-center">
            <label>Size</label>
            <div class="input-group mb-3">
                <div class="input-group-prepend">
                    <button class="btn btn-outline-secondary" type="button" @click.prevent="sizeDown">
                        <i class="fa fa-minus"></i>
                    </button>
                </div>
                <input type="text" class="form-control" :value="fontSize" disabled>
                <div class="input-group-append">
                    <button class="btn btn-outline-secondary" type="button" @click.prevent="sizeUp">
                        <i class="fa fa-plus"></i>
                    </button>
                </div>
            </div>
        </div>

        <Tree :collection="collection"/>
    </div>
</template>

<script>
    // @ is an alias to /src
    import Tree from '@/components/Tree.vue';

    export default {
        components: {
            Tree,
        },
        data () {
            return {
                fontSize: 10,
                collection: {
                    id: 0,
                    team: "First Team",
                    name: "First Employee",
                    designation: "First Designation",
                    employees: [
                        // - Employee1
                        {
                            id: 1,
                            team: "Tech",
                            name: "Employee Name",
                            designation: "Software Engineer",
                            employees: [
                                // - Employee11
                                {
                                    id: 11,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                    employees: [
                                        // - Employee111
                                        {
                                            id: 111,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                            employees: [
                                                // - Employee1111
                                                {
                                                    id: 1111,
                                                    team: "Tech",
                                                    name: "Employee Name",
                                                    designation: "Software Engineer",
                                                    employees: [
                                                        // - Employee11111
                                                        {
                                                            id: 11111,
                                                            team: "Tech",
                                                            name: "Employee Name",
                                                            designation: "Software Engineer",
                                                        },
                                                    ],
                                                },
                                            ],
                                        },
                                    ],
                                },

                                // - Employee12
                                {
                                    id: 12,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                },

                                // - Employee13
                                {
                                    id: 13,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                    employees: [
                                        // - Employee131
                                        {
                                            id: 131,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                            employees: [
                                                // - Employee1311
                                                {
                                                    id: 1311,
                                                    team: "Tech",
                                                    name: "Employee Name",
                                                    designation: "Software Engineer",
                                                },
                                            ],
                                        },
                                        // - Employee132
                                        {
                                            id: 132,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                        },
                                    ],
                                },

                                // - Employee14
                                {
                                    id: 14,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                    employees: [
                                        // - Employee141
                                        {
                                            id: 141,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                        },
                                        // - Employee142
                                        {
                                            id: 142,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                        },
                                    ],
                                },

                                // - Employee15
                                {
                                    id: 15,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                },

                                // - Employee16
                                {
                                    id: 16,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                },
                            ],
                        },

                        // - Employee2
                        {
                            id: 2,
                            team: "Tech",
                            name: "Employee Name",
                            designation: "Software Engineer",
                        },

                        // - Employee3
                        {
                            id: 3,
                            team: "Tech",
                            name: "Employee Name",
                            designation: "Software Engineer",
                            employees: [
                                // - Employee31
                                {
                                    id: 31,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                },

                                // - Employee32
                                {
                                    id: 32,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                    employees: [
                                        // - Employee321
                                        {
                                            id: 321,
                                            team: "Tech",
                                            name: "Employee Name",
                                            designation: "Software Engineer",
                                        },
                                    ]
                                },

                                // - Employee33
                                {
                                    id: 33,
                                    team: "Tech",
                                    name: "Employee Name",
                                    designation: "Software Engineer",
                                },
                            ],
                        },
                    ]
                },
            }
        },
        methods: {
            sizeUp () {
                if (this.fontSize < 99) {
                    this.fontSize++;
                }
            },
            sizeDown () {
                if (this.fontSize >= 5) {
                    this.fontSize--;
                }
            },
        },
    }
</script>
<style lang="scss" scoped>
    * {
        outline:none;
    }
    .flex-center {
        text-align: center;
        display:flex;
        flex-direction: column;
        align-items:center;
        justify-content:center;
        margin: 0 auto;
        margin-bottom: 30px;
        font-size: 16px;
    }
    .input-group {
        position: relative;
        display: -ms-flexbox;
        display: flex;
        -ms-flex-wrap: wrap;
        flex-wrap: wrap;
        -ms-flex-align: stretch;
        align-items: stretch;
        width: auto;
        &-append {
            margin-left: -1px;
        }
        &-prepend {
            margin-right: -1px;
        }
        &-append,
        &-prepend {
            display: -ms-flexbox;
            display: flex;
        }
        input {
            text-align: center;
            width: 50px;
        }
    }

    //*** BOOTSTRAP 4 BUTTON STYLING ***/
    button {
        border-radius: 0;
    }
    button, input, optgroup, select, textarea {
        margin: 0;
        font-family: inherit;
        font-size: inherit;
        line-height: inherit;
    }
    button, input {
        overflow: visible;
    }
    button, select {
        text-transform: none;
    }
    [type=button], [type=reset], [type=submit], button {
        -webkit-appearance: button;
    }
    .btn {
        display: inline-block;
        font-weight: 400;
        color: #212529;
        text-align: center;
        vertical-align: middle;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        background-color: transparent;
        border: 1px solid transparent;
        padding: .375rem .75rem;
        font-size: 1rem;
        line-height: 1.5;
        border-radius: .25rem;
        transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
    }
    .btn-outline-secondary {
        color: #6c757d;
        border-color: #6c757d;
    }
    [type=button]:not(:disabled), [type=reset]:not(:disabled), [type=submit]:not(:disabled), button:not(:disabled) {
        cursor: pointer;
    }
    .input-group-append .btn, .input-group-prepend .btn {
        position: relative;
        z-index: 2;
    }
    .input-group>.input-group-append>.btn, .input-group>.input-group-append>.input-group-text, .input-group>.input-group-prepend:first-child>.btn:not(:first-child), .input-group>.input-group-prepend:first-child>.input-group-text:not(:first-child), .input-group>.input-group-prepend:not(:first-child)>.btn, .input-group>.input-group-prepend:not(:first-child)>.input-group-text {
        border-top-left-radius: 0;
        border-bottom-left-radius: 0;
    }
    .input-group>.input-group-append:last-child>.btn:not(:last-child):not(.dropdown-toggle), .input-group>.input-group-append:last-child>.input-group-text:not(:last-child), .input-group>.input-group-append:not(:last-child)>.btn, .input-group>.input-group-append:not(:last-child)>.input-group-text, .input-group>.input-group-prepend>.btn, .input-group>.input-group-prepend>.input-group-text {
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
    }

    //*** BOOTSTRAP 4 BUTTON FOCUS/ACTIVE ***/
    button:focus {
        outline: 1px dotted;
        outline: 5px auto -webkit-focus-ring-color;
    }
    [type=button]:not(:disabled), [type=reset]:not(:disabled), [type=submit]:not(:disabled), button:not(:disabled) {
        cursor: pointer;
    }
    .btn:hover {
        color: #212529;
        text-decoration: none;
    }
    .btn.focus, .btn:focus {
        outline: 0;
        box-shadow: 0 0 0 0.2rem rgba(0,123,255,.25);
    }
    .btn-outline-secondary:hover {
        color: #fff;
        background-color: #6c757d;
        border-color: #6c757d;
    }
    .btn-outline-secondary.focus, .btn-outline-secondary:focus {
        box-shadow: 0 0 0 0.2rem rgba(108,117,125,.5);
    }
    .input-group-append .btn, .input-group-prepend .btn {
        position: relative;
        z-index: 2;
    }
    .input-group-append .btn:focus, .input-group-prepend .btn:focus {
        z-index: 3;
    }
    .input-group>.input-group-append:last-child>.btn:not(:last-child):not(.dropdown-toggle), .input-group>.input-group-append:last-child>.input-group-text:not(:last-child), .input-group>.input-group-append:not(:last-child)>.btn, .input-group>.input-group-append:not(:last-child)>.input-group-text, .input-group>.input-group-prepend>.btn, .input-group>.input-group-prepend>.input-group-text {
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
    }
    .btn-outline-secondary:not(:disabled):not(.disabled).active, .btn-outline-secondary:not(:disabled):not(.disabled):active, .show>.btn-outline-secondary.dropdown-toggle {
        color: #fff;
        background-color: #6c757d;
        border-color: #6c757d;
    }
    .btn-outline-secondary:not(:disabled):not(.disabled).active:focus, .btn-outline-secondary:not(:disabled):not(.disabled):active:focus, .show>.btn-outline-secondary.dropdown-toggle:focus {
        box-shadow: 0 0 0 0.2rem rgba(108,117,125,.5);
    }

</style>