<template lang="html">
    <div>
        <h1>Homework</h1>
        <ul v-for="item in work" :key="item.sub">
            <li>{{ item.sub }}</li><p>{{ item.work }}:{{ item.det }}<br>End:{{ item.end }}</p>
            <v-divider></v-divider>
        </ul>
    </div>
</template>
<script>
export default {
    data() {
        return {
            work: [
                {sub:"Math",work:"Mid test",det:"Midtest30%",end:"2020/03/12"},
                {sub:"Math",work:"prectice",det:"1 prec",end:"2020/03/12"},
                {sub:"Thai",work:"prectice",det:"1 prec",end:"2020/03/12"},
            ]
        }
    },
    mounted() {
        this.storage();
    },
    methods: {
        storage(){
            this.student_id = sessionStorage.getItem('user_id')
        }        
    },
}
</script>
<style lang="css">
    
</style>