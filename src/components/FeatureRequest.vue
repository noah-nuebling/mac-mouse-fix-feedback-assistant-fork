<template>
    <div class="feature-request">
        <div class="vue-ui-grid col-1 small-gap">

            <!-- Title -->

            <MFFormField
                    :title="i18n('title-title')"
                    :is-required="true"
            >
                <MFInput
                        :placeholder="i18n('title-placeholder-feature')"
                        v-model="attrs.title"
                        autofocus
                        @blur="$emit('findIssues')"
                        required
                />
            </MFFormField>

            <!-- Description -->

            <MFFormField
                    :title="i18n('feature-description-title')"
            >
                <MFInput
                        :placeholder="i18n('feature-description-placeholder')"
                        type="textarea"
                        rows="3"
                        v-model="attrs.description"
                        required
                />
                <!--        <i18n slot="subtitle" id="feature-description-subtitle"/>-->
            </MFFormField>

            <!-- Rationale -->

            <MFFormField
                    :title="i18n('rationale-title')"
            >
                <MFInput
                        :placeholder="i18n('rationale-placeholder')"
                        type="textarea"
                        rows="6"
                        v-model="attrs.rationale"
                        required
                />
                <!--        <i18n slot="subtitle" id="rationale-subtitle"/>-->
            </MFFormField>

            <!--      <MFFormField-->
            <!--        :title="i18n('proposal-title')"-->
            <!--      >-->
            <!--        <MFInput-->
            <!--          placeholder="Describe how you propose to solve the problem and provide code samples of how the API would work once implemented. Note that you can use Markdown to format your code blocks."-->
            <!--          type="textarea"-->
            <!--          rows="4"-->
            <!--          v-model="attrs.proposal"-->
            <!--          -->
            <!--        />-->
            <!--        <i18n slot="subtitle" id="proposal-subtitle"/>-->
            <!--      </MFFormField>-->

            <!-- Additional info -->

            <MFFormField
                    :title="i18n('additional-info-title')"
            >
                <MFInput
                        :placeholder="i18n('additional-info-placeholder-feature')"
                        type="textarea"
                        rows="4"
                        v-model="attrs.additional"
                />

            </MFFormField>

        </div>
    </div>
</template>

<script>
    import {generate} from '../helpers'

    import MFFormField from "./VueUI/MFFormField";
    import MFInput from "./VueUI/MFInput";
    import {emptyReplaced} from "../helpers/emptyReplaced";

    export default {
        components: {
            MFFormField,
            MFInput
        },
        data() {
            return {
                attrs: {
                    title: '',
                    description: '',
                    rationale: '',
                    additional: ''
                },
                label: 'enhancement',
            }
        },

        methods: {
            generate() {

                const a = emptyReplaced(this.attrs, '–')
                const {description, rationale, additional} = a

                return generate(`
## Description
${description}

## Rationale
${rationale}

## Additional info
${additional}
  `.trim())
            }
        }
    }
</script>

<style lang="stylus" scoped>

</style>