<script>
  import { data } from "./lib/movies";
  import Navbar from "./lib/components/Navbar.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import Movies from "./lib/components/Movies.svelte";
  import Event from "./lib/components/Event.svelte";
  import SearchBar from "./lib/components/SearchBar.svelte";

  const handleLike = (i) => {
    data[i].likeCount += 1;
  };
  let isModal = false;
  let selectedMovie = 0;

  const closeModal = () => {
    isModal = !isModal;
  };
  let isEvent = true;
  const handleEvent = () => {
    isEvent = false;
  };
</script>

<Navbar />
{#if isEvent}
  <Event {handleEvent} />
{/if}
<SearchBar />
<Movies {data} bind:selectedMovie {closeModal} {handleLike} />
{#if isModal}
  <Modal {data} {selectedMovie} {closeModal} />
{/if}
