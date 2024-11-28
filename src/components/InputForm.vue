<template>
  <form @submit.prevent="calculate">
    <div>
      <label for="weight">Вес (кг):</label>
      <input type="number" v-model="weight" id="weight" required />
    </div>
    <div>
      <label for="height">Рост (см):</label>
      <input type="number" v-model="height" id="height" required />
    </div>
    <div>
      <label for="activity">Активность:</label>
      <select v-model="activity" id="activity">
        <option value="1.2">Малая активность</option>
        <option value="1.375">Лёгкие тренировки</option>
        <option value="1.55">Средняя активность</option>
        <option value="1.725">Высокая активность</option>
        <option value="1.9">Очень высокая активность</option>
      </select>
    </div>
    <button type="submit">Рассчитать</button>
  </form>
  <div v-if="calories">
    <p>Суточная норма калорий: {{ calories }} ккал</p>
    <p>Белки: {{ protein }} г</p>
    <p>Жиры: {{ fats }} г</p>
    <p>Углеводы: {{ carbs }} г</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      weight: null,
      height: null,
      activity: 1.2,
      calories: null,
      protein: null,
      fats: null,
      carbs: null,
    };
  },
  methods: {
    calculate() {
      // Расчёт калорий по формуле Харриса-Бенедикта
      const bmr = 10 * this.weight + 6.25 * this.height - 5 * 30 + 5; // для мужчин
      this.calories = Math.round(bmr * this.activity);

      // Расчёт БЖУ
      this.protein = Math.round((this.calories * 0.3) / 4); // 30% на белки
      this.fats = Math.round((this.calories * 0.25) / 9); // 25% на жиры
      this.carbs = Math.round((this.calories * 0.45) / 4); // 45% на углеводы
    },
  },
};
</script>
