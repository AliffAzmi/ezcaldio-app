<script lang="ts">
  import Icon from "@iconify/svelte";
  import { Canvas } from "@threlte/core";
  import { Suspense, Text } from "@threlte/extras";

  import activities from "$lib/data/activities.js";

  import Modal from "$lib/components/modal.svelte";
  import CheckBoxBtn from "$lib/components/checkboxBtn.svelte";
  import Scene from "$lib/components/scenes/scale.svelte";

  let gender = "male";
  let calory_needed = "";
  let exercise_point = 1.2;
  let loading = false;
  let showModal = false;
  $: exercise = "no_exercise";
  $: weight = "";
  $: height = "";
  $: age = "";
  $: gender_point = gender === "male" ? 5 : gender === "female" ? 161 : 5;

  const bmr_calculator = () => {
    return (10 * weight + 6.25 * height - 5 * age + gender_point) * exercise_point;
  };

  const handleCaloryCal = async () => {
    loading = true;
    calory_needed = await bmr_calculator();
    handleToggleModal();
    loading = false;
  };

  const handleGender = (gen) => {
    gender = gen;
  };

  const handleToggleModal = () => {
    showModal = !showModal;
  };
</script>

<!-- Calories
The Basal Metabolic Rate (BMR)=

10 * weight (kg) + 6.25 * height(cm) - 5 * age(y) + 5 for (man)

10 * weight(kg) + 6.25 * height(cm) - 5 * age(y) - 161 for ​(woman)

To determin​e your total daily calorie needs, multiply your BMR by the appropriate activity factor, as follows:

If you are sedentary (little or no exercise) : Calorie-Calculation = BMR x 1.2
If you are lightly active (light exercise/sports 1-3 days​/week) : Calorie-Calculation = BMR x 1.375
If you are moderately active (moderate exercise/sports 3-5 days/week) : Calorie-Calculation = BMR x 1.55
If you are very active (hard exercise/sports 6-7 days a week) : Calorie-Calculation = BMR x 1.725
If you are extra active (very hard exercise/sports & physical job or 2x training) : Calorie-Calculation = BMR x 1.9
For example If you are sedentary, and your BMR equal 1745 so the total number of calories you need in order to maintain your current weight = 1745*1.2 = 2094. -->

<div class="inset-0 bg-inherit w-full h-80">
  <Canvas>
    <Scene />
  </Canvas>
  <!-- <div class="relative">
    <Canvas>
      <Suspense>
        <Text color="black" text={`Calory: ${calory_needed}`} fontSize={1.2} textAlign="left" />
      </Suspense>
    </Canvas>
  </div> -->
</div>

<div class="min-h-screen flex items-center justify-center pb-12 px-4 sm:px-6 lg:px-8">
  <div class="max-w-2xl w-full space-y-8">
    <form on:submit|preventDefault={handleCaloryCal} class="space-y-6 p-4 rounded-lg">
      <div>
        <!-- <img
          class="mx-auto h-12 w-auto"
          src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
          alt="Workflow"
        /> -->
        <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">How much calories you need everyday?</h2>
        <p class="mt-2 text-center text-sm text-gray-600">
          Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's
          standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to
          make a type specimen book. It has survived not only five centuries, but also the leap into electronic
          typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset
          sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus
          PageMaker including versions of Lorem Ipsum.
          <!-- <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500"> start your 14-day free trial </a> -->
        </p>
      </div>

      <div class="flex flex-col justify-center items-center">
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
          <Icon class="h-5 w-5 text-gray-400" icon="fluent-mdl2:calendar-year" />
          <input
            class="pl-2 outline-none border-none"
            type="number"
            id="age"
            bind:value={age}
            placeholder="Age"
            required
          />
        </div>
        <div class="flex items-center border-2 py-2 px-3 rounded-2xl mb-4">
          <Icon class="h-5 w-5 text-gray-400" icon="gg:format-line-height" />
          <input
            class="pl-2 outline-none border-none"
            type="number"
            id="height"
            bind:value={height}
            placeholder="Height"
            required
          />
          <span class=" text-xs text-gray-400">CM</span>
        </div>
        <div class="flex items-center border-2 py-2 px-3 rounded-2xl mb-4">
          <Icon class="h-5 w-5 text-gray-400" icon="iconoir:weight-alt" />
          <input
            class="pl-2 outline-none border-none"
            type="number"
            id="weight"
            bind:value={weight}
            placeholder="Weight"
            required
          />
          <span class=" text-xs text-gray-400">KG</span>
        </div>

        <h2 class="mt-6 text-center text-xl font-bold text-gray-900">Activity</h2>
        <!-- <div class="w-full flex flex-wrap justify-center gap-3 cursor-pointer"> -->
        <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 place-items-center gap-3 cursor-pointer">
          {#each activities as activity (activity.id)}
            <div
              class="w-100 text-center border border-gray-300 rounded-lg p-2 cursor-pointer hover:shadow-lg {exercise ===
              activity.value
                ? 'bg-blue-300 border-gray-300'
                : ''}"
            >
              <!-- style="flex: 0 0 calc(50% - 20px);" -->
              <input
                type="radio"
                name={activity.value}
                id={activity.value}
                value={activity.value}
                class="peer hidden"
                bind:group={exercise}
                on:change={() => (exercise_point = activity.point)}
              />
              <label for={activity.value} class="cursor-pointer">
                <img src={activity.icon} alt={activity.name} />
                <span class=" text-xs font-semibold {exercise === activity.value ? 'text-white' : 'text-gray-500'}">
                  {@html activity.name}
                </span>
              </label>
            </div>
          {/each}
        </div>
      </div>
      <div class="text-center">
        <button
          class=" p-2 px-10 {loading ? 'bg-blue-300' : 'bg-blue-500'} rounded-xl text-white font-bold uppercase"
          type="submit"
          disabled={loading ? true : false}>{loading ? "Calculating..." : "Calculate"}</button
        >
      </div>
    </form>
  </div>
</div>
<Modal title="Your calories needed per day" open={showModal} on:close={() => handleToggleModal()}>
  <svelte:fragment slot="body">
    {#if calory_needed}
      <div class="text-center">
        <p class=" text-xl font-bold text-gray-500">{parseInt(calory_needed)} calories</p>
      </div>
    {/if}
  </svelte:fragment>
</Modal>
