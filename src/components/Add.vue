<template>
    <div>

        <div class="add" :class="{'hide':!addShow}">

            <h3>添加地址</h3>
            <div class="container">
                <input type="text" id="addrId" placeholder="addressId" v-model="list.addressId">
                <input type="text" id="addrUser" placeholder="userName" v-model="list.userName">
                <input type="text" id="addrStreet" placeholder="streetName" v-model="list.streetName">
                <input type="text" id="addrCode" placeholder="postCode" v-model="list.postCode">
                <input type="text" id="addrTel" placeholder="tel" v-model="list.tel">
                <input type="text" id="addrIs" placeholder="isDefault" v-model="list.isDefault">
            </div>
            <div class="btnGroup">
                <a class="btn btn--m" href="javascript:;" @click="add">确认</a>
                <a class="btn btn--m btn--red" href="javascript:;" @click="closeAdd">关闭</a>
            </div>
        </div>
        <div :class="{'md-overlay':addShow}" @click="closeAdd"></div>
    </div>
</template>
<script>
    export default {
        name: "add",
        data() {
            return {
                list: [{
                    "addressId": "",
                    "userName": "",
                    "streetName": "",
                    "postCode": "",
                    "tel": "",
                    "isDefault": ""
                }]

            }
        },
        props: [
            'addShow'
        ],
        // watch:{
        //     list(){
        //         console.log(this.list.addrId)
        //     }
        // },
        methods: {
            closeAdd() {
                this.$emit('closeAdd')
            },
            add() {
                // console.log(this.list)
                this.$emit('add', this.list);
                this.$emit('closeAdd');
                this.list=[]

            }
        }
    }
</script>
<style scoped>
    .hide {
        display: none;
    }

    .add {
        position: absolute;
        top: 200px;
        left: 400px;
        background: #fff;
        width: 400px;
        margin: 0 auto;
        padding: 10px 20px;
        text-align: center;
        z-index: 201;
    }

    input {
        width: 300px;
        height: 40px;
        padding-left: 5px;
        margin: 10px;
    }
</style>