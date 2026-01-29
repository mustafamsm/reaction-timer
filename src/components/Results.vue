<template>
    <p>Reaction time - {{ score }}</p>

    <p class="rank"> Your Rank: {{ rank }}</p>
</template>



<script>
export default {
    name: 'Results',
  
    props: ['score'],
    data() {
        return {
            rank:null
        }
    },
    mounted(){
        this.calculateRank();
    },
    methods: {
        calculateRank(){
            if(this.score < 200){
                this.rank = 'Excellent';
            } else if(this.score < 300){
                this.rank = 'Good';
            } else if(this.score < 400){
                this.rank = 'Average';
            } else {
                this.rank = 'Needs Improvement';
            }
        }
    }
};
</script>
<style>
.rank {
    font-weight: bold;
    color:rgb(30, 137, 153);
    
    margin-top: 10px;
}
</style>