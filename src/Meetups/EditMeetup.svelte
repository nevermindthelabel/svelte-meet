<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import TextInput from '../UI/TextInput.svelte';
  import Button from '../UI/Button.svelte';
  import Modal from '../UI/Modal.svelte';
  let title = '';
  let subtitle = '';
  let image = '';
  let address = '';
  let email = '';
  let description = '';

  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch('save-event', {
      title,
      subtitle,
      image,
      address,
      email,
      description
    });
    title = '';
    subtitle = '';
    image = '';
    address = '';
    email = '';
    description = '';
  }
</script>

<Modal title="Add Meetup" on:cancel>
  <form on:submit|preventDefault={submitForm}>
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
    <!-- <Button type="submit">Save Meetup</Button> -->
  </form>
</Modal>

<style>
  form {
    width: 100%;
  }
</style>
