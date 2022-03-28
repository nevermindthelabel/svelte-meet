<script lang="ts">
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  import TextInput from './UI/TextInput.svelte';
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
      <TextInput id="title" label="Title" value={title} on:input={e => (title = e.target.value)} />
      <TextInput id="subtitle" label="Subtitle" value={subtitle} on:input={e => (subtitle = e.target.value)} />
      <TextInput id="image" label="Image URL" value={image} on:input={e => (image = e.target.value)} />
      <TextInput id="address" label="Address" value={address} on:input={e => (address = e.target.value)} />
      <TextInput id="email" type="email" label="Email" value={email} on:input={e => (email = e.target.value)} />
      <TextInput
        id="description"
        label="Description"
        controlType="textarea"
        rows="3"
        value={description}
        on:input={e => (description = e.target.value)}
      />
      <button>Save Meetup</button>
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
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
