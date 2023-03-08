<template lang="html">
    <div>
       <v-row>
        <v-col cols="9" >
            <v-card>
                <h2>จำนวนบุคคลทั้งหมด</h2>
                <canvas id="myChart" style="width:100%;max-width:700px"></canvas>
            </v-card>
        </v-col>
        <v-col cols="3">
            <v-card>
                <h2>จำนวนครู</h2>
                <h2>จำนวนนักเรียน</h2>
            </v-card>
        </v-col>
        <v-col cols="6">
            <v-card>
                <h2><v-icon>mdi-account-school-outline</v-icon>จำนวนนักเรียน</h2>
            </v-card>
        </v-col>
        <v-col cols="6">
            <v-card>
                <h2><v-icon>mdi-human-male-board</v-icon>จำนวนครู</h2>
            </v-card>
        </v-col>
       </v-row>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    layout: 'admin',
    data() {
        return {
        }
    },

}
</script>
<style lang="css"></style>