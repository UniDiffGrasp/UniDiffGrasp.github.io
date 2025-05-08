<script setup>
import { ref } from 'vue';
import abstract from '../mds/abstract.mdx'; 


const imageGallery = ref([
  {
    id: 1, 
    src: './logo.png', 
    caption: 'Fig. 1. UniDiffGrasp: Open-Vocabulary Constrained Grasping Exampleand Performance Comparison. UniDiffGrasp innovatively applies a VLMguided
 part diffusion strategy, achieving state-of-the-art open-vocabularypart grasping and uniquely extending this precision to complex dualarmcooperation.
Its uniffed end-to-end framework, integrating single anddual-arm capabilities, demonstrates exceptional real-world performance and strong generalization.
'
  },
  {
    id: 2,
    src: './logo.png',
    caption: 'Fig. 2. UniDiffGrasp Framework: Integrating VLM Reasoning, Multi-Stage Segmentation, and Part-Guided Diffusion for Grasp Generation. User input
(e.g., ’I’d like to stew some soup’) and visual context are ffrst processed by a VLM (GPT-4o) to determine the target object (’pot’), functional part (’handle’),
and operation mode (’dual-arm’). Multi-stage segmentation—Grounded SAM for object localization and VLPart for precise part identiffcation—then grounds
these semantic targets into geometric constraints. Finally, these constraints guide the Part-Guided Diffusion strategy, employing the dual-arm coordination
method (Sec. III-C) to deffne distinct target regions (e.g., for each handle of the pot) and select stable cooperative grasps.
'
  },
  {
    id: 3,
    src: './logo.png', 
    caption: 'Fig. 3. Principle of Dual-Arm Grasp Generation in UniDiffGrasp usingCoordinated Part-Guided Diffusion
'
  }
]);

</script>

<template>
  <div>
    <!-- 第一部分：摘要 -->
    <el-divider />
    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <!-- 渲染导入的 abstract 组件 -->
            <abstract />
        </el-col>
    </el-row>

    <!-- 第二部分：图片展示 -->
    <el-divider>
      <!-- 可选：为分隔线添加标题 -->
      <span class="divider-text">图片展示</span>
    </el-divider>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <!-- 循环遍历图片数据 -->
            <div v-for="image in imageGallery" :key="image.id" class="image-item">
              <!-- 使用 el-card 包裹，提供阴影和边框效果 -->
              <el-card shadow="hover" class="image-card">
                 <!-- 显示图片 -->
                 <img :src="image.src" :alt="image.caption" class="gallery-image"/>
                 <!-- 图片下方的文字说明容器 -->
                 <div class="caption-container">
                   <p class="caption-text">{{ image.caption }}</p>
                 </div>
              </el-card>
            </div>
        </el-col>
    </el-row>

  </div>
</template>

<style scoped>
.image-item {
  margin-bottom: 24px; /* 图片卡片之间的垂直间距 */
  text-align: center; /* 使卡片内容居中 */
}

.image-card {
  /* 可以给卡片本身添加一些样式，如果需要的话 */
  border-radius: 8px; /* 轻微的圆角 */
}

.gallery-image {
  max-width: 100%; /* 确保图片适应卡片宽度 */
  height: auto;    /* 保持图片的宽高比 */
  display: block;  /* 移除图片下方的额外空白 */
  margin: 0 auto 12px auto; /* 水平居中图片，并与下方文字保持间距 */
  border-radius: 4px; /* 给图片本身也加一点圆角 */
  background-color: #f5f7fa; 
}

.caption-container {
  padding: 0 10px; 
}

.caption-text {
  font-size: 14px;
  color: #606266;     
  line-height: 1.5;  
  margin: 0;        
  text-align: center; 
}

.divider-text {
  font-size: 1.1em;
  color: #909399; /* Element Plus 的提示性文字颜色 */
  font-weight: 500;
}

/* 如果需要调整 el-card 的内边距 */
:deep(.el-card__body) {
    padding: 15px; /* 根据需要调整卡片内部的 padding */
}
</style>
