<script>
  // @ts-nocheck

  import { createEventDispatcher } from "svelte";

  // @ts-nocheck

  const dispatch = createEventDispatcher();

  let userName;
  let userEmail;
  let selectColor;
  let hobbies = [];

  const submitForm = () => {
    const person = {
      name: userName,
      email: userEmail,
      color: selectColor,
      hobbies: hobbies,
    };

    dispatch("personData", person);
    // console.log(userName, userEmail, hobbies, selectColor);
  };
</script>

<h1>Forms in Svelte</h1>
<form on:submit|preventDefault={submitForm}>
  <input type="text" placeholder="Name" bind:value={userName} />
  <input type="text" placeholder="email" bind:value={userEmail} />

  <!-- <h1>{userName}</h1> -->

  <!-- how to bind checkboxes in svelte  -->
  <br />
  <br />
  <label for="">Hobbies</label><br />
  <input type="checkbox" bind:group={hobbies} value="Book Reading" />Book
  Reading <br />
  <input type="checkbox" bind:group={hobbies} value="Gardening" />Gardening<br
  />
  <input type="checkbox" bind:group={hobbies} value="Traveling" />Traveling<br
  />
  <input type="checkbox" bind:group={hobbies} value="Coding" />Coding <br />

  <!-- how to bind checkboxes in svelte  -->

  <!-- how to bind selectboxes in svelte  -->
  <label for="">Select Color</label>
  <select bind:value={selectColor}>
    <option value="black">black</option>
    <option value="red">red</option>
    <option value="green">green</option>
    <option value="blue">blue</option>
  </select>
  <!-- how to bind selectboxes in svelte  -->

  <button type="submit">Submit Form</button>
</form>

<style></style>
