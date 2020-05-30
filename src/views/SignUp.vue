<template>
    <div>

        <v-container>
            <v-row>
                <v-col>
                    <h1>Sign Up</h1>
                <v-form>
                    <v-text-field type="email" label="email" />
                    <v-autocomplete label="Select Browser" :items="browsers" />
                    <v-file-input label="Attach Picture" />
                    <v-text-field label="Select Birthday" v-model="birthday" readonly />
                    <v-date-picker v-model="birthday" />
                    <v-checkbox label="Agree to T & C" />
                    <v-btn type="submit" color="primary">Submit</v-btn>
                </v-form>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
export default {
  data: () => ({
    birthday: "",
    browsers: ["Chrome", "Safari", "Edge", "Safari"]
  })
};
</script>

<style lang="scss" scoped>
</style>