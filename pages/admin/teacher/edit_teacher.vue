<template lang="heml">
    <div>
        <h2>EDIT TEACHER</h2>
        <v-form>
            <v-row>
                <v-col>
                    <v-text-field v-model="first" color="primary" label="Student ID" variant="underlined"></v-text-field>
                    <v-text-field v-model="first" color="primary" label="password" variant="underlined" type="password"></v-text-field>
                    <v-text-field v-model="first" color="primary" label="First name" variant="underlined"></v-text-field>
                    <v-text-field v-model="first" color="primary" label="Last name" variant="underlined"></v-text-field>
                    <v-radio-group v-model="inline" inline label='Gender'>
                      <v-radio label="Male" value="M"></v-radio>
                      <v-radio label="Female" value="F"></v-radio>
                    </v-radio-group>
                    <v-text-field v-model="first" color="primary" label="Bathday" variant="underlined" type="date"></v-text-field>
                    <v-text-field v-model="first" color="primary" label="nationality" variant="underlined"></v-text-field>
                  </v-col>
                  <v-col>
                  <v-text-field v-model="first" color="primary" label="Father first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Father last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Mother first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Mother last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Parent first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Parent last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first" color="primary" label="Phone number of parent" variant="underlined"></v-text-field>
                </v-col>
            </v-row>
            <v-btn color="success" class='mx-3'>submit</v-btn>
            <v-btn color="red">clear</v-btn>
            <v-btn color="warning">Back</v-btn>
        </v-form>
    </div>
</template>
<script>
export default {
  layout: 'admin',
  data() {
    return {
      inline: null,
    }
  },
}
</script>
<style lang="css"></style>