<template>
  <span v-if="displayQuality()" :class="qualities[type].color.text" class="font-bold">{{ qualities[type].title }}</span>
</template>

<script setup lang="ts">

import type { LaneQuality } from '~/types';

const { displayQuality } = useConfig();

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
    title: 'Dangereux',
    color: {
      text: 'text-[#FF0000]'
    }
  },
  bad: {
    title: 'Non satisfaisant',
    color: {
      text: 'text-[#770000]'
    }
  },
  fair: {
    title: 'À améliorer',
    color: {
      text: 'text-[#ff9c9c]'
    }
  },
  good: {
    title: 'Satisfaisant',
    color: {
      text: 'text-[#007700]'
    }
  },
  perfect: {
    title: 'Parfait',
    color: {
      text: 'text-[#00FF00]'
    }
  },
  unknown: {
    title: 'Inconnue',
    color: {
      text: 'text-[#000000]'
    }
  }
};
</script>
