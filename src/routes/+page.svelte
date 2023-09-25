<script lang="ts">
  import Icon from "@iconify/svelte";

  import FullScreenBlock from "$lib/components/fullscreenBlock.svelte";

  function handleAnchorClick(event) {
    event.preventDefault();
    const link = event.currentTarget;
    const anchorId = new URL(link.href).hash.replace("#", "");
    const anchor = document.getElementById(anchorId);
    window.scrollTo({
      top: anchor.offsetTop,
      behavior: "smooth",
    });
  }
</script>

<div class=" flex flex-col justify-center items-center h-screen snap-y">
  <div class="p-6 text-center">
    <p>
      <b>Lorem ipsum</b> dolor sit amet, consectetur adipiscing elit. Integer at tincidunt arcu. Aenean vitae feugiat eros,
      ac vestibulum tortor. Vivamus vitae ex nec odio accumsan luctus. Nunc tempus purus ac erat lobortis, ac varius nibh
      efficitur. Suspendisse potenti. In tincidunt magna vel nibh dapibus, eget tempus augue egestas. Cras egestas massa
      sit amet metus ultricies, eu euismod dui sollicitudin. Sed luctus erat quis dolor imperdiet, vitae facilisis ipsum
      varius. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. In hac habitasse platea
      dictumst. Donec hendrerit elit mollis velit fringilla blandit accumsan at mi. Interdum et malesuada fames ac ante ipsum
      primis in faucibus. Nullam nec semper dui. Phasellus quis neque non metus tempus aliquam.
    </p>
  </div>
  <!-- <a class=" btn btn-blue" href="/calorie-calculator" alt="link">Calorie Calulator</a> -->
  <div class="floating">
    <a href="#anchor-idw-calculator" on:click={handleAnchorClick}>
      <Icon width={35} icon="iconoir:page-down" />
    </a>
  </div>
</div>
<FullScreenBlock />

<style>
  .floating {
    animation-name: floating;
    animation-duration: 3s;
    animation-iteration-count: infinite;
    animation-timing-function: ease-in-out;
    margin-left: 30px;
    margin-top: 5px;
  }

  @keyframes floating {
    0% {
      transform: translate(0, 0px);
    }
    50% {
      transform: translate(0, 15px);
    }
    100% {
      transform: translate(0, -0px);
    }
  }
</style>
