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
    <div class="tag-member-selector">
        <div v-if="formMode" class="tag-member-selector-wrap">
            <member-select
                v-model="memberValue"
                :disabled="!editable || disabled"
                :placeholder="placeholder">
            </member-select>
        </div>
        <span v-else class="rf-view-value">{{viewValue}}</span>
        <span v-show="!validateInfo.valid" class="common-error-tip error-info">{{validateInfo.message}}</span>
    </div>
</template>
<script>
    import '@/utils/i18n.js'
    import { getFormMixins } from '@/components/common/RenderForm/formMixins.js'
    import MemberSelect from '@/components/common/Individualization/MemberSelect.vue'
    const attrs = {
        value: {
            type: String,
            required: false,
            default: ''
        },
        disabled: {
            type: Boolean,
            required: false,
            default: false,
            desc: gettext('禁用组件')
        },
        placeholder: {
            type: String,
            required: false,
            default: '',
            desc: 'placeholder'
        }
    }
    export default {
        name: 'TagMemberSelector',
        components: {
            MemberSelect
        },
        mixins: [getFormMixins(attrs)],
        computed: {
            memberValue: {
                get () {
                    return (this.value && this.value.split(',')) || []
                },
                set (val) {
                    this.updateForm(val.join(','))
                }
            },
            viewValue () {
                return this.value || '--'
            }
        }
    }
</script>
