<template lang="">
    <div>
        <v-container>
            <v-combobox
                v-model="select"
                :items="teacher"
                :search-input.sync="search"
                hide-selected
                label="Add some tags"
                small-chips
            >
            </v-combobox>
    {{ select }}
    </v-container>
    </div>
</template>
<script>
export default {
    layout: 'admin',
    data: () => ({
        select: '',
        search: null,
        teacher: []
    }),
    methods: {
    mymethod (x) { alert(x) },
    },
  created () {
    this.mymethod('success');
  },
}
</script>
<style lang="">
</style>