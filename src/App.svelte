<script lang="ts">
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  let title = '';
  let subtitle = '';
  let image = '';
  let address = '';
  let email = '';
  let description = '';

  let dummyMeetups = [
    {
      id: 'meet1',
      title: 'People standing in front of tree meetup',
      subtitle: 'we meet and look at trees and maps',
      description: 'Some of the participants in an OpenStreetMap meetup in Claremont, Western Australia.',
      image:
        'https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/OSM_meetup_in_Claremont.jpg/640px-OSM_meetup_in_Claremont.jpg',
      address: '123 Fake Street',
      email: 'thing@test.com'
    },
    {
      id: 'meet2',
      title: 'Wikidata meetup',
      subtitle: 'we are some data nerds',
      description: 'Participants at the London Wikidata Meetup on May 5',
      image:
        'https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/London_Wikidata_meetup_2%2C_11.jpg/640px-London_Wikidata_meetup_2%2C_11.jpg',
      address: '456 Fake Street',
      email: 'things@test.com'
    }
  ];
  const addMeetup = () => {
    const newMeetup = {
      id: Math.random().toString(),
      title,
      subtitle,
      image,
      address,
      email,
      description
    };
    dummyMeetups = [...dummyMeetups, newMeetup];
  };
</script>

<Header />
<main>
  <section class="form">
    <form on:submit|preventDefault={addMeetup}>
      <div class="form-control">
        <label for="title">Title</label>
        <input bind:value={title} type="text" id="title" />
      </div>
      <div class="form-control">
        <label for="subtitle">Subtitle</label>
        <input bind:value={subtitle} type="text" id="subtitle" />
      </div>
      <div class="form-control">
        <label for="image">Image URL</label>
        <input bind:value={image} type="url" id="image" />
      </div>
      <div class="form-control">
        <label for="address">Address</label>
        <input bind:value={address} type="text" id="address" />
      </div>
      <div class="form-control">
        <label for="email">Email</label>
        <input bind:value={email} type="email" id="email" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea bind:value={description} rows="3" id="description" />
        <button>Save Meetup</button>
      </div>
    </form>
  </section>
  <section class="meetups">
    <MeetupGrid {dummyMeetups} />
  </section>
</main>

<style>
  main {
    margin-top: 5rem;
  }
</style>
