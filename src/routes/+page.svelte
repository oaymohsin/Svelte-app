<script>
  // @ts-nocheck

  import Counter from "./Counter.svelte";
  import welcome from "$lib/images/svelte-welcome.webp";
  import welcome_fallback from "$lib/images/svelte-welcome.png";
  import Modal from "./modal.svelte";
  import SlotComponent from "./slotComponent.svelte";
  import UserForm from "./forms.svelte";

  let source = "Mohsin APp";
  //   ts-ignore ignores the type checking error
  // @ts-ignore
  let number;
  let showModal = false;
  let arr = [
    {
      id: 1,
      name: "Ali Khan",
      country: "Pakistan",
      email: "ali.khan@example.com",
    },
    {
      id: 2,
      name: "Hassan Ahmed",
      country: "Pakistan",
      email: "hassan.ahmed@example.com",
    },
    {
      id: 3,
      name: "Shoaib Akhtar",
      country: "Pakistan",
      email: "shoaib.akhtar@example.com",
    },
    {
      id: 4,
      name: "Sunny ",
      country: "India",
      email: "sunny@example.com",
    },
    {
      id: 5,
      name: "Qasim Ali",
      country: "Pakistan",
      email: "qasim.ali@example.com",
    },
  ];

  let changeVariable = () => {
    source = "Variable Changed";
  };

  // @ts-ignore
  let handleInput = (e) => {
    source = e.target.value;
  };

  // @ts-ignore
  let deleteUser = (id) => {
    arr = arr.filter((user) => user.id !== id);
  };

  const toggleModal = () => {
    showModal = !showModal;
  };


 const userFormHandler=(e)=>{

	console.log(e)
	console.log(e.detail)
 }
</script>

<svelte:head>
  <title>Home</title>
  <meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
  <h1>
    <span class="welcome">
      <picture>
        <source srcset={welcome} type="image/webp" />
        <img src={welcome_fallback} alt="Welcome" />
      </picture>
    </span>

    to your new<br />SvelteKit app
  </h1>

  <h2>
    try editing <strong>{source}</strong>
  </h2>

  <input type="text" name="" id="" on:input={handleInput} />

  <!-- two way data binding using bind:value directive -->
  <input type="text" name="" id="" bind:value={source} />

  <button on:click={changeVariable}>Change Variable</button>

  <Counter />

  <!-- //how to use loop in this svelete template -->
  <!-- we have used user.id to properly link array data with dom element -->
  {#each arr as user (user.id)}
    <h1>{user.name}</h1>
    <p>{user.email}</p>
    <strong>{user.country}</strong>
    <!-- if I want to delete the user from the array data -->

    <!-- if we use method with parenthesis then the function will be invoked immediately before clicking the button  -->
    <!-- <button on:click={deleteUser()}>Delete User</button> -->

    <button on:click={() => deleteUser(user.id)}>Delete User</button>

    <!-- we have used the else keyword. if the array will be empty then the else block will be execute -->
  {:else}
    <p>there are no users to show</p>
  {/each}

  <!-- //how to use loop in this svelete template -->

  <!-- conditonal statements -->

  <br /> <br />
  <br /> <br />

  <hr>
  <h1>Conditonal Statement</h1>
  <p>Enter any Number</p>
  <input type="text" bind:value={number} />

  {#if number > 20}
    <p>number is greater than 20</p>
  {:else if number < 20}
    <p>number is less than 20</p>
  {:else if typeof number != number}
    <p>Please Enter Number</p>
  {/if}

  <!-- conditonal statements -->

  <!-- we can pass data to components through props -->
  <!-- <Modal message="this is a prop message" showModal={true} /> -->

  <!-- Event Forwarding in Svelte  -->

  <button on:click={toggleModal}> Open Modal </button>
  <Modal message="this is a prop message" {showModal} on:click={toggleModal} />

  <!-- Event Forwarding in Svelte  -->

  <!-- Slots in Svelte  -->

  <br /><br /><br />
  <h1>Slots in Svlete</h1>
  <SlotComponent>
    <div>
      <h3>This is the heading</h3>
      <p>This is the body of the card .................</p>

    </div>
    <!-- we also named the slots  -->
    <div slot="buttonDiv">
      <button>Click me</button>
    </div>
  </SlotComponent>

  <!-- Slots in Svelte  -->

<hr><hr><hr>
  <UserForm on:personData={userFormHandler}/>


</section>

<style>
  section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex: 0.6;
  }

  h1 {
    width: 100%;
  }

  .welcome {
    display: block;
    position: relative;
    width: 100%;
    height: 0;
    padding: 0 0 calc(100% * 495 / 2048) 0;
  }

  .welcome img {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    display: block;
  }

  h1{
	color: crimson;
  }
</style>
