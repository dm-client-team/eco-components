<template>
    <div style="width:600px;paddingd:32px">
        <DemoArea title="基本使用">
            <EUploadArea></EUploadArea>
        </DemoArea>

        <DemoArea title="自定义内容">
            <EUploadArea>
                <div class="e-flex-center" style="height:320px;border:4px solid #ccc;border-radius:16px">
                    <span style="font-size:32px;font-weight:bolder">自定义内容</span>
                </div>
            </EUploadArea>
        </DemoArea>

        <DemoArea title="嵌套上传">

            <EUploadArea disable-tip class="new-tip">
                <template #default="{ showTip }">
                    <div
                        :style="{ borderRadius: '15px', height: '320px', borderColor: showTip ? 'darkorange' : '#ccc', borderStyle: 'solid', borderWidth: '3px', padding: '32px' }">
                        <EUploadArea :key="v" v-for="v in [1, 2, 3]" disable-tip class="inner new-tip"
                            style="float:left;margin-right:32px">

                            <template #default="{ showTip }">
                                <div class="e-flex-center"
                                    :style="{ borderRadius: '15px', height: '96px', borderColor: showTip ? 'darkorange' : '#66ccff', borderStyle: 'solid', borderWidth: '3px', width: '96px' }">
                                </div>
                            </template>
                        </EUploadArea>
                    </div>
                </template>
            </EUploadArea>
        </DemoArea>
    </div>
</template>

<script>
import { EUploadArea } from "../index";

export default {
    components: { EUploadArea },

    beforeCreate() {
        import("./i_base");
    },
    methods: {
        upload(file) {
            console.log(file);
            return new Promise((res) => {
                setTimeout(res, 3000);
            });
        },
    },
};
</script>


<style scoped>
.inner {
    --e_upload_area-icon_size: 32px !important;
}

.new-tip {
    --e_upload_area-border: 2px solid transparent !important;
    --e_upload_area-border-show_tip: 2px solid darkorange !important;
}
</style>

<style scoped>
.loading-icon {
    -webkit-animation: spin 1s linear 1s 5 alternate;
    animation: spin 1s linear infinite;
}

@-webkit-keyframes spin {
    from {
        -webkit-transform: rotate(0deg);
    }

    to {
        -webkit-transform: rotate(-360deg);
    }
}

@keyframes spin {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(-360deg);
    }
}
</style>