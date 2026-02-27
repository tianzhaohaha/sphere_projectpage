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
      <h1 class="section-title">SPHERE: Method Overview</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">

        <p>
          We introduce <strong>SPHERE</strong>, an HE-driven regularization that projects editing perturbations onto a sparse space orthogonal to principal weight directions, preserving hyperspherical uniformity while integrating new knowledge.
        </p>

        <!-- Principal Space Estimation -->
        <div class="method-block">
          <h3 class="method-subtitle">Principal Space Estimation</h3>
          <p>Find unit vector <VueLatex expression="v" /> maximizing projected variance:</p>
          <VueLatex expression="v = \arg\max_{\|\hat{v}\|=1} \left( \frac{1}{n} \hat{v}^\top (W^\top W) \hat{v} \right)" display-mode />
          <p>Collect top-<VueLatex expression="r" /> eigenvectors:</p>
          <VueLatex expression="U = [v_{d-r+1}, \ldots, v_d] \in \mathbb{R}^{d \times r}" display-mode />
        </div>

        <!-- Sparse Space Definition -->
        <div class="method-block">
          <h3 class="method-subtitle">Sparse Space Definition</h3>
          <p>Orthogonal complement of <VueLatex expression="U" />:</p>
          <VueLatex expression="P_\perp = I - \alpha U U^\top \in \mathbb{R}^{d \times d}" display-mode />
          <p><VueLatex expression="\alpha=1" />: hard projection; <VueLatex expression="0<\alpha<1" />: soft projection.</p>
        </div>

        <!-- Sparse Space Projection -->
        <div class="method-block">
          <h3 class="method-subtitle">Sparse Space Projection</h3>
          <p>Project perturbation <VueLatex expression="\Delta W" /> onto sparse space:</p>
          <VueLatex expression="\hat{W} = W + \Delta W P_\perp" display-mode />
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

.method-block {
  margin: 25px 0;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
  border-left: 4px solid #42b883;
}

.method-subtitle {
  font-size: 18px;
  font-weight: bold;
  color: #333;
  margin: 0 0 15px 0;
}

.method-block p {
  margin: 10px 0;
  line-height: 1.8;
}
</style>
