<!-- model 模型 -->
<template>
    <div class="container">

        <div class="functions">
            <scatter></scatter>
        </div>
        <div class="functions">
            <heatmap></heatmap>
        </div>
        <div class="functions">
            <od-line></od-line>
        </div>


    </div>
</template>

<script>
    // 导入自己封装的轮播图子组件
    import {mapActions, mapState} from 'vuex'

    import Scatter from '../subcomponents/Scatter.vue'
    import EarthEffect from '../subcomponents/EarthEffect.vue'
    import Load3DTilesBim from '../subcomponents/Load3DTilesBim.vue'

    import Heatmap from '../subcomponents/Heatmap.vue'
    import OdLine from '../subcomponents/OdLine.vue'


    export default {
        data() {
            return {};
        },
        computed: {
            ...mapState(['tabPaneShowState']),

        },
        created() {
            // 选择显示

        },
        methods: {
            async getlunbotu() {
                // 获取轮播图的方法
                const {data} = await this.$http.get("/getlunbo");
                if (data.status === 200) this.lunbotu = data.result;
            }
        },
        components: {
            // 注册子组件
            Scatter,
            EarthEffect,
            Load3DTilesBim,
            Heatmap,
            OdLine

        }
    };
</script>

<style lang="scss" scoped>
    .layer {
        background-color: #f6f6f6;

        border-width: 0.001px;
        border-color: #e2e2e2;

        /*border: solid;*/
    }

    .container{
        display: flex;
        height: 78px;
        .functions {
            margin-left:3px;
            /*border-style:solid;*/
            border-width:1px;
            /*font-size: 20px;*/
            text-align: center;
        }

    }
    .exist {

    }

    .not-exist {
        display: none;
    }


</style>
