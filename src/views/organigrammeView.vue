<template>
    <div id="tree__" ref="tree"></div>
</template>

<script>
import OrgChart from '@balkangraph/orgchart.js'

export default {
    name: 'tree__',
    data() {
        return {
           nodes : [
    { id: 1, name: 'MINISTRE', title: 'CEO', img: 'https://cdn.balkan.app/shared/2.jpg' },
    { id: 2, pid: 1, name: 'SECRETARIAT GENERAL', title: 'Sales Manager', img: 'https://cdn.balkan.app/shared/3.jpg' },
    { id: 3, pid: 1, name: 'CABINET', title: 'Dev Manager', img: 'https://cdn.balkan.app/shared/4.jpg' },
    { id: 4, pid: 1, name: 'PRMP', title: 'PR Manager', img: 'https://cdn.balkan.app/shared/5.jpg' },
    { id: 5, pid: 1, name: 'DIR.COM', title: 'Marketing Director', img: 'https://cdn.balkan.app/shared/6.jpg', tags: ['partner', 'partnerTemplate'] },
    { id: 6, pid: 1, name: 'SP', title: 'Support Manager', img: 'https://cdn.balkan.app/shared/7.jpg', tags: ['partner', 'partnerTemplate'] },
    { id: 7, pid: 1, name: 'CNAPS', title: 'Legal Advisor', img: 'https://cdn.balkan.app/shared/8.jpg', tags: ['partner', 'partnerTemplate'] },
    { id: 8, pid: 1, name: 'DGT', title: 'Operations Manager', img: 'https://cdn.balkan.app/shared/9.jpg', tags: ['partner', 'partnerTemplate'] },
    { id: 9, pid: 1, name: 'DGPE', title: 'Finance Manager', img: 'https://cdn.balkan.app/shared/10.jpg', tags: ['partner', 'partnerTemplate'] },
    { id: 10, pid: 1, name: 'DGFOP', title: 'Product Manager', img: 'https://cdn.balkan.app/shared/11.jpg', tags: ['partner', 'partnerTemplate'] }
],
            options: {
                scaleInitial: 1,
                mode: 'dark',
                enableSearch: false,
                mouseScrool: OrgChart.none,
                nodeBinding: {
                    field_0: "name",
                    img_0: "img"
                },
                tags: {
                    partnerTemplate: {
                        template: "partnerTemplate"
                    }
                }
            }
        }
    },
    methods: {
        mytree: function(domEl) {
            OrgChart.templates.partnerTemplate = Object.assign({}, OrgChart.templates.ana);
            OrgChart.templates.partnerTemplate.size = [60, 60];
            // Customize background color for the partnerTemplate
            OrgChart.templates.partnerTemplate.node = `
                <rect x="0" y="0" height="{h}" width="{w}" fill="#87CEEB" stroke-width="1" stroke="#aeaeae"></rect>
    `;
            const chart = new OrgChart(domEl, this.options);
            chart.load(this.nodes);
        },
        
        getOptions() {
            const searchParams = new URLSearchParams(window.location.search);
            let fit = searchParams.get('fit');
            let scaleInitial = 1;
            if (fit == 'yes') {
                scaleInitial = OrgChart.match.boundary;
            }
            return { scaleInitial };
        }
    },
    mounted() {
        this.options.scaleInitial = this.getOptions().scaleInitial;
        this.mytree(this.$refs.tree);
    }, 
}
</script>

<style scoped>
/* Add your styles here */
</style>
