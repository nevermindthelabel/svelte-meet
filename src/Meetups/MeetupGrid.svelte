<script lang="ts">
  import MeetupItem from './MeetupItem.svelte';
  export let dummyMeetups;
</script>

<section class="meetups">
  {#each dummyMeetups as { title, address, description, image, email, subtitle }}
    <MeetupItem {title} {address} {description} {image} {email} {subtitle} />
  {/each}
</section>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>
