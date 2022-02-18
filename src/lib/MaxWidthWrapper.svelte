<script>
export let className = ''
export { className as class }
</script>

<div class={`maxWidthWrapper ${className}`} {...$$restProps}>
  <slot />
</div>

<style>
.maxWidthWrapper {
  max-width: 1024px;
  padding-left: 32px;
  padding-right: 32px;
  margin-left: auto;
  margin-right: auto;
}
</style>
