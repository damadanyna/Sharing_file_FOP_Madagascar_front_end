<template>
    <div id="tree__" ref="tree"></div>
</template>

<script>

    import OrgChart from '@balkangraph/orgchart.js'

    export default {

        name: 'tree__',
        data() {
            return {
                nodes: [
                    { id: 1, name: "MINISTRE", title: "CEO", img: "https://cdn.balkan.app/shared/2.jpg" },
                            { id: 2, pid: 1, name: "SECRETARIAT GENERAL", title: "Sales Manager", img: "https://cdn.balkan.app/shared/3.jpg" },
                            { id: 3, pid: 1, name: "CABINET", title: "Dev Manager", img: "https://cdn.balkan.app/shared/4.jpg" },
                            { id: 4, pid: 1, name: "PRMP", title: "Dev Manager", img: "https://cdn.balkan.app/shared/4.jpg" },
                            { id: 5, pid: 1, name: "DIR.COM", title: "Dev Manager", img: "https://cdn.balkan.app/shared/4.jpg" },
                            { id: 6, pid: 1, name: "SP", title: "Dev Manager", img: "https://cdn.balkan.app/shared/4.jpg" },
                            { id: 7, pid: 1, name: "CNAPS", title: "Dev Manager", img: "https://cdn.balkan.app/shared/4.jpg" },
                            { id: 8, pid: 2, name: "DGT", title: "Sales", img: "https://cdn.balkan.app/shared/5.jpg" },
                            { id: 9, pid: 2, name: "DGPE", title: "Sales", img: "https://cdn.balkan.app/shared/6.jpg" },
                            { id: 10, pid: 2, name: "DGFOP", title: "Developer", img: "https://cdn.balkan.app/shared/7.jpg" },
                            { id: 11, pid: 2, name: "DRTEFOP", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 12, pid: 2, name: "DAFGP", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 13, pid: 2, name: "DPSSE", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 14, pid: 2, name: "DEAJ", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 15, pid: 2, name: "DSI", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 16, pid: 2, name: "DRHM", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 17, pid: 2, name: "DRTEFOP", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" },
                            { id: 18, pid: 2, name: "DRTEFOP", title: "Developer", img: "https://cdn.balkan.app/shared/8.jpg" }
                ]
            }
        },

        methods: {
            mytree: function(domEl, x) {
                this.chart = new OrgChart (domEl, {
                    nodes: x,
                    nodeBinding: {
                        field_0: "name",
                        img_0: "img"
                    }
                });
            }
        },

        mounted(){
            this.mytree(this.$refs.tree, this.nodes)
        }
    }
</script>

<style scoped>
</style>