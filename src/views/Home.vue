<template>
  <v-container class="elevation-0 my-12 transparent" height="200px">
    <div class="quiz-description">
      <div class="quiz-description__inner">
        <div class="quiz-description__title">【ルール】</div>
        <p class="quiz-description__text">
          スタートすると、画面に「問題」が表示されます。<br>
          入力エリアに「答え」となるワードを入力してください。<br>
          もし「答え」が分からなければ、tabキーで次の「問題」へ進めることができます。
        </p>
        <p class="quiz-description__text">
          制限時間は30〜90秒です。時間内に何個クリア出来たか判定するゲームとなります。<br>
          制限時間経過後のタイムアップ画面にクリア数が表示されます。<br>
          結果をシェアして友人や同僚と競い合おう！
        </p>
      </div>
    </div>
  </v-container>
</template>
<script>
</script>
<style lang="scss">
.quiz-description {
  border: 3px solid #ffedd2;
  border-radius: 25px;
  box-shadow: 0 4px 10px rgb(84 84 84 / 80%);
  color: #fff;
  font-size: 20px;
  margin: 0 auto;
  max-width: 900px;
  padding: 60px 40px;
}
.quiz-description .quiz-description__title {
  color: #f4d099;
  font-size: 2em;
  font-weight: bold;
  line-height: 1;
  margin-bottom: 30px;
  text-align: center;
  text-shadow: 0 0 5px #e00c1b;
}
.quiz-description .quiz-description__text {
  text-align: center;
}
</style>