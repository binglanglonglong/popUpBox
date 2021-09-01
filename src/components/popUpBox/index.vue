<template>
    <div v-if="shows" class="popupbox">
        <div class="boxPopupbox">
            <div class="topline">
                <span>{{msg}}</span>
                <span @click="clickCancel">×</span>
            </div>
            <div class="textboob">
                <div v-for="(item,index) in listss" :key="index">
                    {{item}}
                </div>
            </div>
            <div class="btns">
                <button @click="clickConfirmation">确定</button>
                <button @click="clickCancel">取消</button>
            </div>
        </div>
    </div>
</template>

<script>
import "./index.css"
export default {
    //  msg 是详情, listss 是内容(必须是数组格式)
    props:["msg","listss"],
    data(){
        return {
            shows: false
        }
    },
    methods: {
        // 点击确认
        clickConfirmation(){
            this.bus.$emit("clickConfirmation",true);
            this.shows = false;
        },
        // 点击取消或×
        clickCancel(){
            
            this.shows = false;
        }
        
    },
    mounted(){
        this.bus.$on("comeon",(res)=>{
            this.shows = res;
        })
    }
}
</script>
<style scoped>

</style>