<script>
  import { onMount } from "svelte";
  let count = 0;
  let lastKey = "";

  function handleKeyPress(event) {
    count++;
    lastKey = event.key === " " ? "Space" : event.key;
    highlightKey(event.code, true);
  }

  function handleKeyRelease(event) {
    highlightKey(event.code, false);
  }

  onMount(() => {
    window.addEventListener("keydown", handleKeyPress);
    window.addEventListener("keyup", handleKeyRelease);

    return () => {
      window.removeEventListener("keydown", handleKeyPress);
      window.removeEventListener("keyup", handleKeyRelease);
    };
  });

  function highlightKey(code, isPressed) {
    const keyElement = document.querySelector(`.key[data-code="${code}"]`);
    if (keyElement) {
      if (isPressed) {
        keyElement.classList.add("highlight");
      } else {
        keyElement.classList.remove("highlight");
      }
    }
  }
</script>

<main>
  <h1>Keyboard Counter</h1>
  <p>Press any key to increase the count:</p>
  <p>Count: {count}</p>
  <p class="key-display">Last Key Pressed: {lastKey}</p>

  <div class="keyboard-container">
    <div class="keyboard">
      <!-- Top row (numbers and symbols) -->
      <div class="row">
        <div class="key" data-code="Backquote">~</div>
        <div class="key" data-code="Digit1">1</div>
        <div class="key" data-code="Digit2">2</div>
        <div class="key" data-code="Digit3">3</div>
        <div class="key" data-code="Digit4">4</div>
        <div class="key" data-code="Digit5">5</div>
        <div class="key" data-code="Digit6">6</div>
        <div class="key" data-code="Digit7">7</div>
        <div class="key" data-code="Digit8">8</div>
        <div class="key" data-code="Digit9">9</div>
        <div class="key" data-code="Digit0">0</div>
        <div class="key" data-code="Minus">-</div>
        <div class="key" data-code="Equal">=</div>
        <div class="key large" data-code="Backspace">Backspace</div>
      </div>

      <!-- QWERTY row -->
      <div class="row">
        <div class="key large" data-code="Tab">Tab</div>
        <div class="key" data-code="KeyQ">Q</div>
        <div class="key" data-code="KeyW">W</div>
        <div class="key" data-code="KeyE">E</div>
        <div class="key" data-code="KeyR">R</div>
        <div class="key" data-code="KeyT">T</div>
        <div class="key" data-code="KeyY">Y</div>
        <div class="key" data-code="KeyU">U</div>
        <div class="key" data-code="KeyI">I</div>
        <div class="key" data-code="KeyO">O</div>
        <div class="key" data-code="KeyP">P</div>
        <div class="key" data-code="BracketLeft">[</div>
        <div class="key" data-code="BracketRight">]</div>
        <div class="key" data-code="Backslash">\</div>
      </div>

      <!-- ASDF row -->
      <div class="row">
        <div class="key large" data-code="CapsLock">CapsLock</div>
        <div class="key" data-code="KeyA">A</div>
        <div class="key" data-code="KeyS">S</div>
        <div class="key" data-code="KeyD">D</div>
        <div class="key" data-code="KeyF">F</div>
        <div class="key" data-code="KeyG">G</div>
        <div class="key" data-code="KeyH">H</div>
        <div class="key" data-code="KeyJ">J</div>
        <div class="key" data-code="KeyK">K</div>
        <div class="key" data-code="KeyL">L</div>
        <div class="key" data-code="Semicolon">;</div>
        <div class="key" data-code="Quote">'</div>
        <div class="key large" data-code="Enter">Enter</div>
      </div>

      <!-- ZXCV row -->
      <div class="row">
        <div class="key extra-large" data-code="ShiftLeft">Shift</div>
        <div class="key" data-code="KeyZ">Z</div>
        <div class="key" data-code="KeyX">X</div>
        <div class="key" data-code="KeyC">C</div>
        <div class="key" data-code="KeyV">V</div>
        <div class="key" data-code="KeyB">B</div>
        <div class="key" data-code="KeyN">N</div>
        <div class="key" data-code="KeyM">M</div>
        <div class="key" data-code="Comma">,</div>
        <div class="key" data-code="Period">.</div>
        <div class="key" data-code="Slash">/</div>
        <div class="key extra-large" data-code="ShiftRight">Shift</div>
      </div>

      <!-- Spacebar row -->
      <div class="row">
        <div class="key large" data-code="ControlLeft">Ctrl</div>
        <div class="key large" data-code="MetaLeft">Win</div>
        <div class="key large" data-code="AltLeft">Alt</div>
        <div class="key extra-large" data-code="Space">Space</div>
        <div class="key large" data-code="AltRight">Alt</div>
        <div class="key large" data-code="MetaRight">Win</div>
        <div class="key large" data-code="ContextMenu">Menu</div>
        <div class="key large" data-code="ControlRight">Ctrl</div>
      </div>
    </div>

    <!-- Num Pad -->
    <div class="numpad">
      <div class="row">
        <div class="key large" data-code="NumLock">NumLock</div>
        <div class="key" data-code="NumpadDivide">/</div>
        <div class="key" data-code="NumpadMultiply">*</div>
        <div class="key" data-code="NumpadSubtract">-</div>
      </div>
      <div class="row">
        <div class="key" data-code="Numpad7">7</div>
        <div class="key" data-code="Numpad8">8</div>
        <div class="key" data-code="Numpad9">9</div>
        <div class="key large" data-code="NumpadAdd">+</div>
      </div>
      <div class="row">
        <div class="key" data-code="Numpad4">4</div>
        <div class="key" data-code="Numpad5">5</div>
        <div class="key" data-code="Numpad6">6</div>
      </div>
      <div class="row">
        <div class="key" data-code="Numpad1">1</div>
        <div class="key" data-code="Numpad2">2</div>
        <div class="key" data-code="Numpad3">3</div>
        <div class="key large" data-code="NumpadEnter">Enter</div>
      </div>
      <div class="row">
        <div class="key extra-large" data-code="Numpad0">0</div>
        <div class="key" data-code="NumpadDecimal">.</div>
      </div>
    </div>
  </div>
  <script
    async
    src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-5246141430412355"
    crossorigin="anonymous"
  ></script>
  <!-- CodingBroz Tools -->
  <ins
    class="adsbygoogle"
    style="display:block"
    data-ad-client="ca-pub-5246141430412355"
    data-ad-slot="1974764287"
    data-ad-format="auto"
    data-full-width-responsive="true"
  ></ins>
  <script>
    (adsbygoogle = window.adsbygoogle || []).push({});
  </script>
</main>

<style>
  main {
    text-align: center;
    padding: 1rem;
    font-family: "Comic Sans MS", "Poppins", Arial, Helvetica, sans-serif;
  }
  h1 {
    font-size: 2rem;
    margin-bottom: 1rem;
  }
  p {
    font-size: 1.5rem;
    margin: 0.5rem 0;
  }
  .key-display {
    font-size: 2rem;
    font-weight: bold;
    color: #007bff;
  }
  .keyboard-container {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
  }
  .keyboard {
    display: inline-block;
    margin-right: 1rem;
  }
  .numpad {
    display: inline-block;
  }
  .row {
    display: flex;
    justify-content: center;
    margin-bottom: 0.5rem;
  }
  .key {
    width: 40px;
    height: 40px;
    border: 1px solid #ccc;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 2px;
    border-radius: 4px;
    user-select: none;
  }
  .key.large {
    width: 80px;
  }
  .key.extra-large {
    width: 120px;
  }
  .key.highlight {
    background-color: #007bff;
    color: #fff;
  }
</style>
