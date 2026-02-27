<template>
  <div>
    <el-row justify="center">
      <el-col :xs="24" :sm="22" :md="18" :lg="14" :xl="14">
        <div class="teaser-container">
          <img src="/sphere.png" alt="Teaser Figure" class="teaser-img" />
          <p class="teaser-caption">
            Figure: (a) A weight matrix is viewed as a set of neurons (red dots) on a hypersphere. (b) Current SOTA methods introduce perturbations (blue triangles) that interfere with the principal hyperspherical directions of pre-edit weights. (c) SPHERE projects new knowledge onto a sparse space complementary to the principal hyperspherical directions.
          </p>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.teaser-container {
  margin: 20px 0;
  text-align: center;
}

.teaser-img {
  max-width: 75%;
  border-radius: 8px;
  box-shadow: 1px 1px 4px 1px #afafaf;
}

.teaser-caption {
  margin-top: 12px;
  font-size: 14px;
  color: #666;
  font-style: italic;
  line-height: 1.6;
}
</style>
