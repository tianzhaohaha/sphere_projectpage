<script lang="ts" setup>
import { ref } from 'vue'

const currentRQ = ref(0)

const rqs = [
  {
    id: 'RQ1',
    question: 'How does SPHERE perform on sequential editing tasks compared to baseline methods?',
    image: '/experiments/rq1.png',
    caption: 'Comparison of SPHERE with existing methods on sequential editing. Eff., Gen., Spe., Flu. and Consis. denote Efficacy, Generalization, Specificity, Fluency and Consistency, respectively. The best results are highlighted in bold, while the second-best results are underlined.'
  },
  {
    id: 'RQ2',
    question: 'Can SPHERE effectively preserve the hyperspherical uniformity of edited weights?',
    image: '/experiments/rq2.png',
    caption: 'Cosine similarity between neurons in the updated weight matrix after 15,000 edits. Darker colors indicate lower similarity, reflecting better hyperspherical and orthogonal uniformity. SPHERE effectively preserves the weight structure, demonstrating the most stable hyperspherical uniformity.'
  },
  {
    id: 'RQ3',
    question: 'How does SPHERE-edited LLMs perform on general ability evaluations?',
    image: '/experiments/rq3.png',
    caption: 'General ability testing of post-edited LLaMA3 (8B) on four tasks.Eff. Gen. Spe.'
  },
  {
    id: 'RQ4',
    question: 'Can baseline methods be significantly improved with plug-and-play SPHERE?',
    image: '/experiments/rq4.png',
    caption: 'Performance improvements of baseline editing methods after adding a single line of code from SPHERE (i.e., sparse space projection). Gray bars denote the original baseline performance, while purple bars indicate the performance after enhancement.'
  },
  {
    id: 'RQ5',
    question: 'What is the computational overhead of SPHERE in terms of time efficiency?',
    image: '/experiments/rq5.png',
    caption: 'Runtimes of SPHERE.'
  },
  {
    id: 'RQ6',
    question: 'How do different hyperparameter choices affect the stability of SPHERE?',
    image: '/experiments/rq6.png',
    caption: 'Sensitivity of SPHERE.'
  }
]
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Experiments</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="22" :md="18" :lg="14" :xl="14">

        <!-- 问题列表 -->
        <!-- <ul class="rq-list">
          <li v-for="rq in rqs" :key="rq.id">
            <strong>{{ rq.id }}:</strong> {{ rq.question }}
          </li>
        </ul> -->

        <!-- RQ 选择按钮 -->
        <div class="rq-tabs">
          <el-button
            v-for="(rq, index) in rqs"
            :key="rq.id"
            :type="currentRQ === index ? 'primary' : 'default'"
            size="small"
            @click="currentRQ = index"
          >
            {{ rq.id }}
          </el-button>
        </div>

        <!-- 卡片内容 -->
        <div class="rq-card">
          <h3 class="rq-title">{{ rqs[currentRQ].id }}: {{ rqs[currentRQ].question }}</h3>
          <div class="rq-content">
            <img :src="rqs[currentRQ].image" :alt="rqs[currentRQ].id" class="rq-img" />
            <p class="rq-caption">{{ rqs[currentRQ].caption }}</p>
          </div>
        </div>

      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.section-title {
  font-size: 28px;
  margin: 20px 0;
  text-align: center;
}

.rq-tabs {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}

.rq-card {
  background: #fff;
  border: 1px solid #e4e7ed;
  border-radius: 12px;
  padding: 25px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.08);
}

.rq-title {
  font-size: 18px;
  color: #333;
  margin: 0 0 20px 0;
  text-align: center;
  line-height: 1.5;
}

.rq-content {
  text-align: center;
}

.rq-img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 1px 1px 4px 1px #afafaf;
}

.rq-caption {
  margin-top: 12px;
  font-size: 14px;
  color: #666;
  font-style: italic;
}

.intro-text {
  margin-bottom: 15px;
  line-height: 1.6;
}

.rq-list {
  margin: 0 0 25px 0;
  padding-left: 20px;
  line-height: 1.8;
}

.rq-list li {
  margin-bottom: 8px;
}
</style>
