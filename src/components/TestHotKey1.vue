<template>
    <div class="container" style="">
        <span style="align-items: center;padding: 0 16px;background: #F6F8FE;font-size: 16px">
            <label class="sure">取消 </label> <label id="tip">有效期 </label>
            <label class="sure" style="color: #4A81EE;">确定</label>

        </span>
        <span id="date" style="justify-content: space-around">
            <div class="ip">
                <div class="item" v-for="(e,i) in datas">
                    <label class="title">{{e.title}} </label>
                </div>
            </div>
            <div class="ip">
                <div class="item" v-for="(e,i) in datas">
                    <label class="title">{{e.title}} </label>
                </div>
            </div>
            <div class="ip">
                <div class="item" v-for="(e,i) in datas">
                    <label class="title">{{e.title}} </label>
                </div>
            </div>
            <div class="ip">
                <div class="item" v-for="(e,i) in datas">
                    <label class="title">{{e.title}} </label>
                </div>
            </div>
        </span>
        <div class="line-1" style="margin-top: -100px;margin-bottom: 100px"></div>
        <div class="line-1" style="margin-top: -50px;margin-bottom: 50px"></div>
    </div>
</template>

<script>
    import NumInput from './NumInput';

    export default {
        name: 'home',

        components: {NumInput},

        data() {
            return {
                datas: []
            }
        },
        mounted() {
            for (let i = 0; i < 12; i++) {
                this.datas.push({
                    title: '2019'
                })
            }
        },

        methods: {
            toast() {
                this.$toast.show('toast')
            },

            dialog() {
                this.$dialog.show({
                    head: '标题',
                    showClear: true,
                    body: '内容',
                    cancel: '取消',
                    confirm: '确认',
                    dialog: () => {
                        this.$load.show('确认中...')
                        setTimeout(() => {
                            this.$load.hide()
                        }, 2000)
                    }
                })
            },

            getFn() {
                this.$http.get('/api/test').then(res => {
                    console.log(res)
                }).catch(error => {
                    console.log(error)
                })
            },

            postFn() {
                let data = {}
                this.$http.post('/api/post', data).then(res => {
                    console.log(res)
                }).catch(error => {
                    console.log(error)
                })
            }
        }
    }
</script>

<style scoped lang="scss">
    @import "~styles/extends.scss";

    .container {
        background: #fff;
        text-align: center;
        font-weight: normal;
        font-size: 16px;
        overflow: auto;
        width: 100%;
        color: $theme-black;
        padding: 0px;

        #tip-b {
            margin-right: 16px;
        }

        #tip {
            padding: 10px;
            flex: 1;
            font-size: 16px;
            font-family: PingFangSC-Medium, PingFang SC;
            font-weight: bold;
            color: rgba(54, 61, 78, 1);
            line-height: 25px;
        }

        #date {
            .ip {
                overflow: auto;
                height: 150px;
                flex: 1;

                .item {
                    min-height: 50px;
                    justify-content: center;

                    .title {
                        font-size: 16px;
                        font-family: PingFangSC-Regular, PingFang SC;
                        font-weight: 400;
                        color: rgba(54, 61, 78, 1);
                    }
                }
            }
        }


    }

    .flex {
        @extend %flex-justify-center-between;
    }

    * {
        font-family: PingFangSC-Regular, PingFang SC;
        box-sizing: border-box;
    }

    i {
        font-family: "iconfont" !important;
        font-size: 16px;
        font-style: normal;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    button {
        font-size: 16px;
        font-family: PingFangSC-Medium, PingFang SC;
        font-weight: 500;
        color: rgba(255, 255, 255, 1);
        background: rgba(73, 129, 238, 1);
        border-radius: 8px;
        padding: 10px 32px;
    }

    .c-w {
        color: white !important;
    }

    .c-g {
        color: #363D4E !important;
    }

    .ml-16 {
        margin-left: 16px;
    }

    .line-8 {
        height: 8px;
        background: #F6F8FE;
    }

    .line-1 {
        height: 1px;
        background: #F6F8FE;
    }

    div {
        display: flex;
        flex-direction: column;
    }

    span {
        display: flex;
        flex-direction: row;
    }
</style>
