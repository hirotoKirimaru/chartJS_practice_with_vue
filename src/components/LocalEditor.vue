　<template>
　 <div class="editor">
　 <h1> エディター画面 </h1>
　 <button @click="logout"> ログアウト </button>

   <h3>円グラフを描画する</h3>
   <PieChart class="pieChart" :data="pieChartData" :options="options"></PieChart>
　 </div>
　</template>
　<script>
  import { Pie } from 'vue-chartjs';
  
  var PieChart = {
      extends: Pie,
      mounted(){
          this.renderChart({
            // ラベル
            labels: ["天領", "薩摩", "長州", "土佐"],
            // データ詳細
            datasets: [{
              label: '藩と人口',
              data: [13740000, 9072000, 7150000, 6148000],
              backgroundColor: [
                 'rgba(255, 100, 130, 0.2)',
                 'rgba(100, 130, 255, 0.2)',
                 'rgba(130, 255, 100, 0.2)',
                 'rgba(230, 210, 85, 0.2)'
              ]
          }]
          });
    }
  }

　export default {
　 name: 'editor',
   props: ['user'],
   components: {
    PieChart
   },
   methods: {
     logout: function(){
        firebase.auth().signOut();
     }
   }
　}
　</script>
　<style lang="scss">
  .pieChart{
      width: 80vw;
      height: 80vh;
  }

　</style>
