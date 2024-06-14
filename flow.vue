<template>
  <div class="flowchart-container">
    <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg">
      <g v-for="(node, index) in nodes" :key="index">
        <!-- Node -->
        <rect
          :x="node.x"
          :y="node.y"
          width="150"
          height="50"
          rx="10"
          ry="10"
          fill="#90CAF9"
          stroke="#0D47A1"
          stroke-width="2"
        />
        <!-- Node Text -->
        <text
          :x="node.x + 75"
          :y="node.y + 25"
          text-anchor="middle"
          alignment-baseline="middle"
          fill="#0D47A1"
          font-size="14"
          font-family="Arial"
        >
          {{ node.label }}
        </text>

        <!-- Arrow -->
        <line
          v-if="index < nodes.length - 1"
          :x1="node.x + 150"
          :y1="node.y + 25"
          :x2="node.x + 200"
          :y2="node.y + 25"
          stroke="#0D47A1"
          stroke-width="2"
        />
        <polygon
          v-if="index < nodes.length - 1"
          :points="`${node.x + 200},${node.y + 20} ${node.x + 210},${node.y + 25} ${node.x + 200},${node.y + 30}`"
          fill="#0D47A1"
        />
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'FlowChart',
  data() {
    return {
      nodes: [
        { label: 'Introduction', x: 10, y: 50 },
        { label: 'Literature Review', x: 250, y: 50 },
        { label: 'Methodology', x: 490, y: 50 },
        { label: 'Results', x: 730, y: 50 },
        { label: 'Discussion', x: 970, y: 50 },
        { label: 'Conclusion', x: 1210, y: 50 },
      ],
    };
  },
};
</script>

<style scoped>
.flowchart-container {
  width: 100%;
  overflow-x: scroll;
  white-space: nowrap;
}
</style>
