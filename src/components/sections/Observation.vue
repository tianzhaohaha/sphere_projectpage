<script lang="ts">
import { defineComponent } from 'vue'
import { VueLatex } from 'vatex'

export default defineComponent({
  components: {
    VueLatex
  }
})
</script>

<template>
  <div>
    <el-divider />

    <!-- 主标题 -->
    <el-row justify="center">
      <h1 class="section-title">Correlation Between Angular (HE) and Editing?</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">

        <!-- 第一部分：实证分析 -->
        <h2 class="subsection-title">Empirical Observation</h2>
        
        <p>
          <strong>Observation 1: Collapse in sequential editing is closely tied to sharp fluctuations in HE.</strong> 
          <!-- Figure 1 reveals a strong correlation between HE dynamics and editing performance. The Spearman correlation scores between HE and each editing metric, displayed at the end of each curve, consistently indicate a strong statistical dependence before model collapse. Most methods collapse well before 3,000 edits, whereas AlphaEdit demonstrates the strongest long-term editing capacity with the best preservation of hyperspherical uniformity. A closer examination of the metrics shows a consistent pattern in which each drop in performance is consistently accompanied by rapid shifts in HE, underscoring its central role in maintaining sequential editing stability. -->
        </p>

        <!-- 图片1 -->
        <div class="figure-container">
          <img src="/observation/OBS_1.png" alt="Figure 1" class="figure-img" />
          <p class="figure-caption">Figure 1: Trends of HE and editing performance throughout sequential editing. The Spearman correlation scores between HE and each editing metric displayed at the end of each curve.</p>
        </div>

        <p>
          <strong>Observation 2: Advanced editing methods suppress HE fluctuations effectively.</strong> 
          <!-- Figure 3 illustrates the correlation between changes in HE (ΔHE) and editing performance (ΔAcc.), where each point denotes the difference between two consecutive batch edits: points near the origin indicate greater stability with minimal variation in both HE and accuracy, while points farther away reflect larger fluctuations and less stable editing. Most advanced methods exhibit tightly clustered distributions near the origin, indicating stable editing dynamics and minimal weight distortion. Furthermore, we fit a linear regression over all points across metrics, which demonstrates a statistically significant positive correlation between ΔHE and ΔAcc. in terms of Efficacy and Generalization. This suggests a strong positive correlation between editing stability and HE stability, implying that the effectiveness of SOTA approaches may stem from their ability to suppress HE fluctuations. -->
        </p>

        <!-- 图片2 -->
        <div class="figure-container">
          <img src="/observation/OBS_2.png" alt="Figure 2" class="figure-img" />
          <p class="figure-caption">Figure 2: Correlation between changes in HE and editing performance across consecutive edited weights. Each point corresponds to a ∆HE–∆Acc. pair for one method over five thousand sequential edits. Confidence ellipses and regression lines illustrate overall trends.</p>
        </div>


        <!-- 第二部分：理论分析 -->
        <h2 class="subsection-title">Theoretical Analysis</h2>

        <div class="theorem-box">
          <div class="theorem-header">
            <span class="theorem-label">Theorem 1</span>
            <span class="theorem-name">(Lower Bound on Output Perturbation)</span>
          </div>
          <div class="theorem-content">
            <p><em>Under the assumptions of orthonormal inputs and small perturbations, the output perturbation ΔV is lower-bounded by squared change in HE:</em></p>
            <VueLatex expression="|\Delta V| \geq \left( \frac{\Delta HE}{K} \right)^2" display-mode />
            <p><em>where</em></p>
            <VueLatex expression="K = 4 \left( \sum_{k=1}^{p} \left( \sum_{j \neq k} \| w_k - w_j \|^{-3} \right)^2 \right)^{1/2}" display-mode />
            <p><em>and K is a constant dependent on the original weight matrix geometry.</em></p>
          </div>
        </div>

        <p>
          This theorem reveals a key insight: the change in HE (|ΔHE|) inevitably induces a substantial output perturbation (ΔV), meaning that edits that significantly distort the geometric arrangement of neurons are bound to corrupt pretrained knowledge. This result provides a solid theoretical foundation for our empirical findings and underscores HE as a fundamental indicator of editing stability.
        </p>

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

.subsection-title {
  font-size: 22px;
  margin: 30px 0 15px 0;
  color: #333;
  border-bottom: 2px solid #eee;
  padding-bottom: 8px;
}

.figure-container {
  margin: 25px 0;
  text-align: center;
}

.figure-img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 1px 1px 4px 1px #afafaf;
}

.figure-caption {
  margin-top: 10px;
  font-size: 14px;
  color: #666;
  font-style: italic;
}

/* 学术论文风格定理框 */
.theorem-box {
  margin: 25px 0;
  border: 2px solid #333;
  border-radius: 0;
  background: #fafafa;
  overflow: hidden;
}

.theorem-header {
  background: #333;
  color: #fff;
  padding: 10px 15px;
  font-size: 16px;
}

.theorem-label {
  font-weight: bold;
  margin-right: 8px;
}

.theorem-name {
  font-style: italic;
  font-weight: normal;
}

.theorem-content {
  padding: 20px;
  line-height: 1.8;
}

.theorem-content p {
  margin: 10px 0;
}

.formula-block {
  margin: 20px 0;
  padding: 15px;
  background: #f9f9f9;
  border-radius: 8px;
  border-left: 4px solid #409eff;
}
</style>
