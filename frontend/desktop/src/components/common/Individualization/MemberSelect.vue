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
    <bk-user-selector
        v-model="setValue"
        :api="api"
        :placeholder="placeholder"
        :disabled="disabled"
        :search-limit="maxResult"
        :multiple="multiple"
        :tag-clearable="hasDeleteIcon"
        :fixed-height="fixedHeight"
        @change="change"
        @select-user="select"
        @remove-selected="remove">
    </bk-user-selector>
</template>
<script>
    import BkUserSelector from '@blueking/user-selector'
    export default {
        name: 'MemberSelect',
        components: { BkUserSelector },
        model: {
            prop: 'value',
            event: 'change'
        },
        props: {
            value: {
                type: Array,
                default: () => ([])
            },
            placeholder: String,
            disabled: {
                type: Boolean,
                default: false
            },
            hasDeleteIcon: {
                type: Boolean,
                default: true
            },
            multiple: {
                type: Boolean,
                default: true
            },
            maxData: {
                type: Number,
                default: -1
            },
            maxResult: {
                type: Number,
                default: 5
            }
        },
        data () {
            return {
                fixedHeight: false,
                api: `${window.MEMBER_SELECTOR_DATA_HOST}/api/c/compapi/v2/usermanage/fs_list_users/`
            }
        },
        computed: {
            setValue: {
                get () {
                    return this.value
                },
                set (val) {
                    this.$emit('change', val)
                }
            }
        },
        methods: {
            change (tags) {
                this.$emit('change', tags)
            },
            select (tag) {
                this.$emit('select', tag)
            },
            remove (tag) {
                this.$emit('remove', tag)
            }
        }
    }
</script>
<style lang="scss" scoped>
    .tag-member-selector-wrap {
        .user-selector {
            width: 100%;
        }
    }
</style>
