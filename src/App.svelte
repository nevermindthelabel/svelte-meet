<script lang="ts">
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  const dummyMeetups = [
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
</script>

<Header />
<main>
  <MeetupGrid {dummyMeetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }
</style>
