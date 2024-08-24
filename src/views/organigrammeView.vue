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
                { id: 1, name: 'MINISTRE' },
                { id: 2, pid: 1, name: 'SECRETARIAT GENERAL' },
                { id: 3, pid: 1, name: 'CABINET' },
                { id: 4, pid: 1, name: 'PRMP' },
                { id: 5, pid: 1, name: 'DIR.COM'   },
                { id: 6, pid: 1, name: 'SP'},
 
                { id: 7, pid: 4, name: 'UGPM'  },
                { id: 8, pid: 2, name: 'DGT' },
                { id: 9, pid: 2, name: 'DGPE'},
                { id: 10, pid: 2, name: 'DGFOP' },
 
                { id: 11, pid: 2, name: 'DRTEFOP', tags: ['partner', 'partnerTemplate'] }, 
                { id: 12, pid: 2, name: 'DAFGP', tags: ['partner', 'partnerTemplate'] }, 
                { id: 13, pid: 2, name: 'DPSSE', tags: ['partner', 'partnerTemplate'] },
                { id: 14, pid: 2, name: 'DEAJ', tags: ['partner', 'partnerTemplate'] },
                { id: 15, pid: 2, name: 'DSI', tags: ['partner', 'partnerTemplate'] },
                { id: 16, pid: 2, name: 'DRHM', tags: ['partner', 'partnerTemplate'] },
 
                { id: 17, pid: 8, name: 'DSST' },
                { id: 18, pid: 8, name: 'DPTD'},
                { id: 19, pid: 8, name: 'DMP'},
                { id: 20, pid: 8, name: 'DTPDF'},
                
                { id: 21, pid: 9, name: 'DFCR'},
                { id: 22, pid: 9, name: 'DPAIJSE'},
                { id: 23, pid: 9, name: 'DPPMPAE'},
                
                { id: 24, pid: 10, name: 'DRHE'},
                { id: 25, pid: 10, name: 'DFPAE'},
                { id: 26, pid: 10, name: 'DRFP'},
                { id: 27, pid: 10, name: 'DEPED'},


            ],
            options: {
                scaleInitial: 0.5, // Smaller scale to fit the container
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
        mytree(domEl) {
            OrgChart.templates.partnerTemplate = Object.assign({}, OrgChart.templates.ana);
            OrgChart.templates.partnerTemplate.size = [160, 100];

            OrgChart.templates.partnerTemplate.node = `
                <rect x="0" y="0" height="{h}" width="{w}" fill="rgb(3, 155, 229)" stroke-width="1" stroke="#aeaeae"></rect>
             `;

            const chart = new OrgChart(domEl, this.options);
            chart.load(this.nodes);
        },
        getOptions() {
            const searchParams = new URLSearchParams(window.location.search);
            let fit = searchParams.get('fit');
            let scaleInitial = 0.5; // Smaller initial scale
            if (fit === 'yes') {
                scaleInitial = OrgChart.match.boundary;
            }
            return { scaleInitial };
        }
    },
    mounted() {
        this.options.scaleInitial = this.getOptions().scaleInitial;
        this.mytree(this.$refs.tree);
    }
}
</script>

<style scoped>
#tree__ {
    width: 100%; /* Define a smaller width for the container */
    height: 100%; /* Define a smaller height for the container */
    overflow: hidden;
}
</style>
