<script setup lang="ts">
const props = defineProps<{
  icon: string
  size?: 'sm' | 'md' | 'lg'
  hasTooltip?: boolean
  darkModeText?: boolean
  withTransition?: boolean
  ariaLabel?: string
  disabled?: boolean
}>()

const sizeClasses = {
  sm: 'p-1',
  md: 'p-2',
  lg: 'p-3',
}

const iconSizeClasses = {
  sm: 'h-4 w-4',
  md: 'h-5 w-5',
  lg: 'h-6 w-6',
}
</script>

<template>
  <button
    class="flex flex-row items-center justify-center gap-2 rounded-lg p-2 text-gray-900 hover:bg-neutral-100 dark:text-gray-100 dark:hover:bg-neutral-800"
    :class="[
      sizeClasses[size ?? 'md'],
      disabled ? 'cursor-not-allowed opacity-50' : '',
      hasTooltip ? 'group relative' : '',
      withTransition ? 'transition-colors duration-300' : '',
    ]"
    :aria-label="ariaLabel"
    :disabled="disabled"
  >
    <div
      :class="[
        iconSizeClasses[size ?? 'md'],
        props.icon,
        darkModeText ? 'text-gray-900 dark:text-gray-100' : '',
        withTransition ? 'transition-colors duration-300' : '',
      ]"
    />
    <slot />
  </button>
</template>
