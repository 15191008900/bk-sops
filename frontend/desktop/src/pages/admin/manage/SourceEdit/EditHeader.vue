/**
* Tencent is pleased to support the open source community by making 蓝鲸智云PaaS平台社区版 (BlueKing PaaS Community
* Edition) available.
* Copyright (C) 2017-2021 THL A29 Limited, a Tencent company. All rights reserved.
* Licensed under the MIT License (the "License"); you may not use this file except in compliance with the License.
* You may obtain a copy of the License at
* http://opensource.org/licenses/MIT
* Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
* an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
* specific language governing permissions and limitations under the License.
*/
<template>
    <div class="edit-header">
        <div :class="['step-item', {
            'active': $route.name === 'packageEdit',
            'finished': $route.name === 'cacheEdit'
        }]">
            <div class="step-content">
                <div class="num">1</div>
                <div class="title">{{ $t('配置') + $t('主包源') }}</div>
            </div>
        </div>
        <div :class="['step-item', {
            'active': $route.name === 'cacheEdit'
        }]">
            <div class="step-content">
                <div class="num">2</div>
                <div class="title">{{ $t('配置') + $t('本地缓存') }}</div>
            </div>
        </div>
    </div>
</template>
<script>

    export default {
        name: 'EditHeader'
    }
</script>
<style lang="scss" scoped>
    .edit-header {
        position: relative;
        padding-top: 16px;
        height: 70px;
        border-bottom: 1px solid #cacedb;
        box-shadow: 0 3px 4px 0 rgba(64,112,203,0.06);
        overflow: hidden;
        z-index: 101;
    }
    .step-item {
        float: left;
        position: relative;
        width: 50%;
        font-size: 12px;
        &:first-child {
            left: 0;
            padding-left: 80px;
            &:after {
                content: '';
                position: absolute;
                top: 6px;
                left: 96px;
                width: calc(100% - 88px);
                height: 4px;
                background: #e1e4eb;
            }
            .title {
                left: 0;
                text-align: left;
                padding-left: 60px;
            }
        }
        
        &:last-child {
            right: 0;
            padding-right: 80px;
            text-align: right;
            &:after {
                content: '';
                position: absolute;
                top: 6px;
                right: 94px;
                width: calc(100% - 80px);
                height: 4px;
                background: #e1e4eb;
            }
            .title {
                right: 0;
                text-align: right;
                padding-right: 50px;
            }
        }
        &.active {
            .step-content {
                .num {
                    color: #3a84ff;
                    background: #ffffff;
                    border: 2px solid #3a84ff;
                }
                .title {
                    color: #3a84ff;
                }
            }
            &:after {
                background: #3a84ff;
            }
        }
        &.finished {
            .step-content {
                .num {
                    color: #3a84ff;
                    background: #3a84ff;
                    border: 2px solid #3a84ff;
                }
                .title {
                    color: #3a84ff;
                }
            }
            &:after {
                background: #3a84ff;
            }
        }
        .step-content {
            display: inline-block;
            text-align: center;
            .num {
                display: flex;
                justify-content: center;
                align-items: center;
                margin: 0 auto;
                width: 16px;
                height: 16px;
                background: #e1e4e8;
                color: #ffffff;
                border-radius: 50%;
            }
            .title {
                position: absolute;
                margin-top: 10px;
                color: #313238;
                width: 100%;
            }
        }
    }
</style>
