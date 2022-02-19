<script>
import { defaultSkinColor, defaultClothesColor } from '$lib/constants'
import Character from '$lib/Character'
import MaxWidthWrapper from '$lib/MaxWidthWrapper.svelte'
import ControlPane from '$lib/ControlPane.svelte'

import {
  bodyOptions,
  headOptions,
  faceOptions,
  accessoryOptions,
  skinColorOptions,
  clothesColorOptions,
} from './helpers'

let body = 0,
  head = 0,
  face = 0,
  accessory = 0,
  skinColor = defaultSkinColor,
  clothesColor = defaultClothesColor
</script>

<div class="bar-background" />
<main class="characterEditor">
  <MaxWidthWrapper>
    <header class="header">
      <h1 class="title">Create your Character</h1>
      <p class="description">
        Customize your character's look and style using the controls below. What sort of adventure will you embark on?{' '}
      </p>
    </header>
    <div class="controlColumn">
      <ControlPane title="Bodies" options={bodyOptions} bind:currentOption={body} />
      <ControlPane title="Heads" options={headOptions} bind:currentOption={head} />
      <ControlPane title="Faces" options={faceOptions} bind:currentOption={face} />
      <ControlPane title="Accessories" options={accessoryOptions} bind:currentOption={accessory} />
      <ControlPane title="Skin Color" options={skinColorOptions} bind:currentOption={skinColor} />
      <ControlPane title="Clothing Color" options={clothesColorOptions} bind:currentOption={clothesColor} />
    </div>
  </MaxWidthWrapper>

  <div class="characterWrapper">
    <Character {body} {head} {face} {accessory} {skinColor} {clothesColor} />
  </div>
</main>

<style>
.characterEditor {
  padding-top: 128px;
  padding-bottom: 64px;
}

.characterEditor > :global(.maxWidthWrapper:first-child) {
  position: relative;
}

header {
  padding-bottom: 64px;
  width: 65%;
}

.title {
  font-size: 2.5rem;
  font-weight: 600;
  margin-top: 0;
  margin-bottom: 16px;
  letter-spacing: -0.5px;
}

.description {
  font-size: 1.25rem;
  margin: 0;
}

.characterWrapper {
  min-height: 500px;
  position: fixed;
  left: 65%;
  width: 35%;
  top: 10%;
}

.controlColumn {
  width: 50%;
}

.bar-background {
  position: fixed;
  width: 100%;
  height: 40%;
  bottom: 0;
  background-color: hsl(195deg, 20%, 86%);
}
</style>
