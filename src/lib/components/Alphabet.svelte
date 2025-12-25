<script lang="ts">
  const LETTERS = [
    { letter: "a", sound: "ah" },
    { letter: "b", sound: "ba" },
    { letter: "c", sound: "ka" },
    { letter: "d", sound: "da" },
    { letter: "e", sound: "e" },
    { letter: "f", sound: "fä" },
    { letter: "g", sound: "ga" },
    { letter: "h", sound: "ha" },
    { letter: "i", sound: "ii" },
    { letter: "j", sound: "jah" },
    { letter: "k", sound: "ka" },
    { letter: "l", sound: "lah" },
    { letter: "m", sound: "ma" },
    { letter: "n", sound: "na" },
    { letter: "o", sound: "oh" },
    { letter: "p", sound: "pa" },
    { letter: "q", sound: "qa" },
    { letter: "r", sound: "ra" },
    { letter: "s", sound: "sa" },
    { letter: "t", sound: "ta" },
    { letter: "u", sound: "ah" },
    { letter: "v", sound: "vah" },
    { letter: "w", sound: "wa" },
    { letter: "x", sound: "exa" },
    { letter: "y", sound: "ya" },
    { letter: "z", sound: "za" },
  ];

  let index = 0;

  const speakLetter = (i: number) => {
    const utter = new SpeechSynthesisUtterance();
    utter.text = LETTERS[i].sound;
    speechSynthesis.speak(utter);
  };

  const handleSelect = (i: number) => {
    index = i;
    speakLetter(i);
  };
</script>

<div class="wrapper">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="primary" on:click={() => speakLetter(index)}>
    {LETTERS[index].letter}
  </div>
  <div class="buttons">
    {#each LETTERS as l, i}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div
        class="button"
        class:active={i === index}
        on:click={() => handleSelect(i)}
      >
        {l.letter}
      </div>
    {/each}
  </div>
</div>

<style>
  .wrapper {
    padding: 35px 5px;
    display: flex;
    flex: 1;
    flex-direction: column;
  }

  .primary {
    display: flex;
    flex: 1;
    align-items: center;
    justify-content: center;
    font-size: 300px;
    line-height: 1;
    cursor: pointer;
    font-family: "Comic Sans MS", cursive, sans-serif;
  }

  .buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .button {
    display: flex;
    width: 45px;
    height: 45px;
    margin: 5px;
    border-radius: 5px;
    align-items: center;
    justify-content: center;
    font-size: 30px;
    cursor: pointer;
    line-height: 1;
    font-family: "Comic Sans MS", cursive, sans-serif;
    color: #ffffff;
    background: rgb(30, 110, 208);
  }

  .button:hover,
  .button.active {
    background: rgb(208, 30, 137);
  }
</style>
