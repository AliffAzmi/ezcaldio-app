<script lang="ts">
  import Icon from "@iconify/svelte";

  import CheckBoxBtn from "$lib/components/checkboxBtn.svelte";

  let formula_point = 0.45;
  let gender_point = 0;
  let gender = "male";
  let height_measurement = "inch";
  let result = 0;
  let loading = false;

  $: height = "";
  $: gender_point = gender === "male" ? -3 : -2;

  const handleGender = (gen) => {
    gender = gen;
  };

  const handleIDWCal = async () => {
    loading = true;
    result = await idwCalculator();
    loading = false;
  };

  const idwCalculator = async () => {
    let new_height = height;
    let new_height_ = height_measurement === "cm" ? parseInt(new_height * 0.393701) : new_height;
    return new_height_ * formula_point + gender_point;
  };

  const cm2inch = () => {
    if (height_measurement === "inch") {
      height = parseInt(height * 0.393701);
    } else {
      height = parseInt(height * 2.54);
    }
  };
</script>

<!-- IDW = Height in inch * .45 + F/M 
    Female point = -2
    Male point = -3-->
<div class="p-4">
  <div>
    <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">Ideal Waist Calculator (IDW)</h2>
    <p class="mt-2 text-center text-sm text-gray-600">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's
      standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a
      type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting,
      remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing
      Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions
      of Lorem Ipsum.
    </p>
  </div>

  <form on:submit|preventDefault={handleIDWCal} class="space-y-6 p-4 rounded-lg">
    <div class="grid w-auto grid-cols-2 gap-2 rounded-xl bg-gray-200 p-2 mb-4">
      <div class=" flex flex-col flex-grow items-center w-100">
        <Icon class="w-8 h-8" icon="mdi:face-male-outline" />
        <CheckBoxBtn text={"male"} {gender} on:click={() => handleGender("male")} />
      </div>
      <div class=" flex flex-col flex-grow items-center w-100">
        <Icon class="w-8 h-8" icon="mdi:face-female-outline" />
        <CheckBoxBtn text={"female"} {gender} on:click={() => handleGender("female")} />
      </div>
    </div>

    <div class="flex items-center border-2 py-2 px-3 rounded-2xl mb-4">
      <Icon class="h-5 w-5 text-gray-400" icon="gg:format-line-height" />
      <input
        class="pl-2 outline-none border-none w-full"
        type="number"
        id="height"
        bind:value={height}
        placeholder="Height"
        required
      />
      <span class=" text-xs text-gray-400">
        <select bind:value={height_measurement} on:change={cm2inch}>
          <option value="inch">INC</option>
          <option value="cm">CM</option>
        </select>
      </span>
    </div>

    <div class="text-center">
      <button
        class=" p-2 px-10 {loading ? 'bg-blue-300' : 'bg-blue-500'} rounded-xl text-white font-bold uppercase"
        type="submit"
        disabled={loading ? true : false}>{loading ? "Calculating..." : "Calculate"}</button
      >
    </div>

    {#if result}
      <p class=" text-center">
        Your ideal waist for your height is <b>{parseFloat(result).toFixed(2)}</b> inches.
      </p>
    {/if}
  </form>
</div>
