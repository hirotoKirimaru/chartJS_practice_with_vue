　<template>
　 <div class="editor">
　 <h1> エディター画面 </h1>
　 <button @click="logout"> ログアウト </button>
   <div>
     <p>カラム名:</p>

     <div> 
       <input type="text" value="カラム名">
       <input type="text" value="値">
     </div>
     <div v-for="(label, index) in customPieData.labels" :key="label"> 
       <input type="text" v-model="customPieData.labels[index]">
       <input type="text" v-model="customPieData.datasets[0].data[index]">
     </div>
   </div>

   <h3>円グラフを描画する</h3>
   <CustomPie :data="customPieData" :options="customPieOptions"></CustomPie>
　 </div>
　</template>
　<script>
  import CustomPie from '@/template/CustomPie.vue'

　export default {
　 name: 'editor',
   props: ['user'],
   components: {
    CustomPie
   },
   data: function(){
     return{
       customPieData:{
        labels: ['未実施', '仕掛中', '障害発生', '完了'],
        datasets: [{
          data: [350, 100, 5, 20],
          backgroundColor: [
            'rgba(255, 100, 130, 0.2)',
            'rgba(100, 130, 255, 0.2)',
            'rgba(130, 255, 100, 0.2)',
            'rgba(230, 210, 85, 0.2)'
          ]
        }]
        },
        customPieOptions: {
          cutoutPercentage: 0,
          rotation: -0.5 * Math.PI,
          circumference: 2 * Math.PI,
          'animation.animateRotate': true,
          'animation.animateScale': false
        },
      }
   },
   options: {
     title: {
        display: true,
        text: 'テスト進捗状況'
     }
   },
   methods: {
     logout: function(){
        firebase.auth().signOut();
     }
   }
　}
　</script>
