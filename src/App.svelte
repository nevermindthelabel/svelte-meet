<script lang="ts">
  import Header from './UI/Header.svelte';
  import Button from './UI/Button.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  import EditMeetup from './Meetups/EditMeetup.svelte';

  let editMode = false;

  let dummyMeetups = [
    {
      id: 'meet1',
      title: 'People standing in front of tree meetup',
      subtitle: 'we meet and look at trees and maps',
      description: 'Some of the participants in an OpenStreetMap meetup in Claremont, Western Australia.',
      image:
        'https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/OSM_meetup_in_Claremont.jpg/640px-OSM_meetup_in_Claremont.jpg',
      address: '123 Fake Street',
      email: 'thing@test.com',
      isFavorite: false
    },
    {
      id: 'meet2',
      title: 'Wikidata meetup',
      subtitle: 'we are some data nerds',
      description: 'Participants at the London Wikidata Meetup on May 5',
      image:
        'https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/London_Wikidata_meetup_2%2C_11.jpg/640px-London_Wikidata_meetup_2%2C_11.jpg',
      address: '456 Fake Street',
      email: 'things@test.com',
      isFavorite: false
    }
  ];

  const addMeetup = (e: CustomEvent) => {
    const newMeetup = {
      id: Math.random().toString(),
      title: e.detail.title,
      subtitle: e.detail.Subtitle,
      image: e.detail.image,
      address: e.detail.address,
      email: e.detail.email,
      description: e.detail.description,
      isFavorite: false
    };
    dummyMeetups = [...dummyMeetups, newMeetup];
    editMode = false;
  };

  function toggleFavorite(e: CustomEvent) {
    const id = e.detail;
    const updateMeetupFav = { ...dummyMeetups.find(meetup => meetup.id === id) };
    updateMeetupFav.isFavorite = !updateMeetupFav.isFavorite;
    const meetupIndex = dummyMeetups.findIndex(meet => meet.id === id);
    const updatedMeetups = [...dummyMeetups];
    updatedMeetups[meetupIndex] = updateMeetupFav;
    dummyMeetups = updatedMeetups;
  }

  function toggleEdit() {
    editMode = !editMode;
  }

  function cancelEdit() {
    editMode = null;
  }
</script>

<Header />
<main>
  <section class="meetups">
    <div class="padding">
      <Button on:click={toggleEdit}>Add Meetup</Button>
    </div>
    {#if editMode}
      <EditMeetup on:save-event={addMeetup} on:cancel={cancelEdit} />
    {/if}
    <MeetupGrid {dummyMeetups} on:toggle-favorite={toggleFavorite} />
  </section>
</main>

<style>
  main {
    margin-top: 5rem;
  }
  .padding {
    padding: 1rem;
  }
</style>
