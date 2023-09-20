<script>
  export let text = "";
  export let gender = "";
  let checked = false;
  if (gender === text) {
    checked = true;
  }
</script>

<div>
  <input type="radio" name="option" id={text} class="peer hidden" {checked} on:click />
  <label
    for={text}
    class="block cursor-pointer select-none rounded-xl p-2 px-10 text-center peer-checked:bg-blue-500 peer-checked:font-bold peer-checked:text-white uppercase"
    >{text}</label
  >
</div>
