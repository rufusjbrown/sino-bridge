<template>
    <section class="container">
        <b-field>
            <b-input placeholder="Name"
                icon="account">
            </b-input>
        </b-field>

        <b-field>
            <b-input placeholder="Email"
                type="email"
                icon="email">
            </b-input>
        </b-field>

        <b-field label="Experience">
            <b-select placeholder="Select">
                <option value="0">0 Years</option>
                <option value="1">0 - 1 Years</option>
                <option value="2">1 - 2 Years</option>
                <option value="3">2 - 5 Years</option>
                <option value="4">5+ Years</option>
            </b-select>
        </b-field>

        <b-field label="Subjects">
            <b-taginput
                v-model="tags"
                :data="filteredTags"
                autocomplete
                :allow-new="allowNew"
                icon="label"
                placeholder="Add a tag"
                @typing="getFilteredTags">
            </b-taginput>
        </b-field>
    </section>
</template>

<script>
    const data = ['English', 'Mathematics', 'Physics']//require('@/data/sample.json')

    export default {
        data() {
            return {
                filteredTags: data,
                isSelectOnly: false,
                tags: [],
                allowNew: false,                
            }
        },
        methods: {
            getFilteredTags(text) {
                this.filteredTags = data.filter((option) => {
                    return option
                        .toString()
                        .toLowerCase()
                        .indexOf(text.toLowerCase()) >= 0
                })
            }
        }
    }
</script>