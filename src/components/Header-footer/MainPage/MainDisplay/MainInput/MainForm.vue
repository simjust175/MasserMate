<template>
    <v-card color="bg-green-lighten-2 pa-2" theme="light" height="431">
        <v-tabs v-model="tab" class="bg-white" hide-slider stacked grow>
            <v-tab value="1" :class="{ 'bg-grey-lighten-3': tab == 1 }" :ripple="false">
                <v-icon icon="mdi mdi-hand-coin-outline"></v-icon>
            </v-tab>

            <v-tab value="2" :class="{ 'bg-grey-lighten-3': tab == 2 }" :ripple="false">
                <v-icon icon="mdi mdi-finance"></v-icon>
            </v-tab>

        </v-tabs>

        <v-tabs-window v-model="tab">
            <v-tabs-window-item value="1">
                <main-form-text-field inputMethod="charity"/>
            </v-tabs-window-item>

            <v-tabs-window-item value="2">
                <main-form-text-field inputMethod="income"/>
            </v-tabs-window-item>
        </v-tabs-window>
    </v-card>
</template>

<script>
import MainFormTextField from './MainFormTextField.vue'
export default {
    components: { MainFormTextField },
    data() {
        return {
            tab: null
        }
    },
}
</script>

<style></style>