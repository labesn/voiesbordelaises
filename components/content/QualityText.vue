<template>
  <span v-if="displayQuality()" :class="qualities[type].color.text" class="font-bold">{{ qualities[type].title }}</span>
</template>

<script setup lang="ts">

import type { LaneQuality } from '~/types';

const { displayQuality } = useConfig();
const { qualityNames } = useStats();

const { type } = defineProps<{
  type: LaneQuality
}>();

type QualityText = {
  [key in LaneQuality]: {
    title: string;
    color: {
      text: string;
    }
  }
}
const qualities: QualityText = {
  dangerous: {
    title: qualityNames.dangerous,
    color: {
      text: 'text-[#FF0000]'
    }
  },
  bad: {
    title: qualityNames.bad,
    color: {
      text: 'text-[#770000]'
    }
  },
  fair: {
    title: qualityNames.fair,
    color: {
      text: 'text-[#ff9c9c]'
    }
  },
  good: {
    title: qualityNames.good,
    color: {
      text: 'text-[#007700]'
    }
  },
  perfect: {
    title: qualityNames.perfect,
    color: {
      text: 'text-[#00FF00]'
    }
  },
  unknown: {
    title: qualityNames.unknown,
    color: {
      text: 'text-[#000000]'
    }
  }
};
</script>
