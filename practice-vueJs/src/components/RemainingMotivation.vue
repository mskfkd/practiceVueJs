<script setup>
// ① Vue から何を import するか
// ・ユーザー操作で変わる値に必要なもの
// ・派生状態に必要なもの
import { computed, ref } from 'vue';


// ② このアプリで「中心になる状態」は何か
// ・数値の範囲は？
// ・なぜ ref にするのか
const motivationNum = ref(50); 


// ③ 数値から導かれる「表示用の情報」は何か
// ・状態ラベル（文字列）
// ・バーの色
// ・危険状態かどうか
// → これらはなぜ computed が適しているか
const importStatusDisplay = computed(()=> {
  if (motivationNum.value >= 70) {
    return "今ならなんでもできそう";
  } else if (motivationNum.value >= 30) {
    return "ご褒美が必要"
  } else {
    return "返事がない。しかばねのようだ。"
  }
});


// ④ 状態分岐の境界値を決める
// ・高い / 普通 / 低い の基準
// ・この値を変えると UI にどう影響するか
const motivationWidth = computed(() => {
  return motivationNum.value + '%';
});


</script>

<template>
  <!-- ⑤ アプリ全体のコンテナ -->
  <div class="appContainer">
    <!-- ⑥ タイトル表示 -->
     <h1>🔋やる気残量あぷり</h1>
    <!-- ⑦ 残量メーター枠 -->
     <div class="displayMeter">
      <!-- ⑧ 実際に伸び縮みするバー -->
      <!-- ・width は何を元に決めるか -->
      <!-- ・色はどこから来るか -->
      <!-- ・危険時にだけ付く class は何か -->
       <div class="meterBar" :style="{ width: motivationNum }"></div>
    <!-- ⑨ 数値と状態ラベルの表示 -->
    <!-- ・なぜ直接計算せず、用意した値を表示するのか -->
      <p>やる気残量：{{ motivationNum }} %</p>
      <p>状態： {{ importStatusDisplay }}</p>
     </div>

  </div>




    <!-- ⑩ ユーザー操作部分 -->
    <!-- ・どの値と v-model で結びつくか -->
    <!-- ・操作すると何が連鎖的に変わるか -->

</template>

<style scoped>
/* ⑪ 常に適用される見た目 */
.displayMeter {
  width: 300px;
  border: 1px solid #ccc;
}

.meterBar {
  height: 20px;
  background-color: green;
  transition: width 0.3s ease;
}
/* ⑫ メーターの枠のスタイル */

/* ⑬ バーの基本スタイル */
/* ・アニメーションを滑らかにする工夫 */

/* ⑭ 危険状態専用のスタイル */
/* ・なぜ style ではなく class なのか */

/* ⑮ アニメーション定義（任意） */
</style>
