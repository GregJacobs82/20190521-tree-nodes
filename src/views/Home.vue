<template>
    <div class="home">
        <div
            class="row"
            v-for="employee in collection"
            :key="employee.id"
        >
            <Node
                :id="employee.id"
                :team="employee.team"
                :name="employee.name"
                :designation="employee.designation"
                :employees="employee.employees"
            />
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import Node from '@/components/Node.vue'

    export default {
        name: 'home',
        components: {
            Node
        },
        data () {
            return {
                collection: [

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
            }
        }
    }
</script>
<style scoped lang="scss">
    .row {
        margin-bottom: 2em;
    }
</style>