<script>
import ToggleButton from '$lib/ToggleButton.svelte'
import ButtonRow from '$lib/ButtonRow.svelte'

export let title, options, currentOption
</script>

<div class="controlPane">
  <h2 class="title">
    {title}

    <span class="metadata">
      {options.length} options
    </span>
  </h2>
  <ButtonRow>
    {#each options as { id, label, color, children }}
      <ToggleButton key={id} isSelected={currentOption === id} on:click={() => (currentOption = id)} {label} {color}>
        {children || ''}
      </ToggleButton>
    {/each}
  </ButtonRow>
</div>

<style>
.controlPane {
  padding: 24px;
  /* Optical centering */
  padding-top: 18px;
  background-color: white;
  border-radius: 8px;
  /*
    HACK: Margin on an outer bound like this is
    a little gross, but we haven't seen the tools
    to deal with it yet!
  */
  margin-bottom: 32px;
}

.title {
  margin: 0;
  /* Optical centering */
  margin-bottom: -4px;
}

.metadata {
  margin-left: 16px;
  font-size: 0.875rem;
  font-weight: 400;
  color: hsl(0deg, 0%, 30%);
}
</style>
