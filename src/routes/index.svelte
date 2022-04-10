<script>
  import { fade } from 'svelte/transition';
  let form = { submitted: false };
  let rating;

  function updateRating() {
    rating = parseInt(this.textContent);
  }

  function handleSubmit() {
    if (!rating) return;
    form.submitted = true;
  }
</script>

<main>
  {#if !form.submitted}
    <div class="card fade">
      <div class="icon">
        <svg width="17" height="16" xmlns="http://www.w3.org/2000/svg"><path d="m9.067.43 1.99 4.031c.112.228.33.386.58.422l4.45.647a.772.772 0 0 1 .427 1.316l-3.22 3.138a.773.773 0 0 0-.222.683l.76 4.431a.772.772 0 0 1-1.12.813l-3.98-2.092a.773.773 0 0 0-.718 0l-3.98 2.092a.772.772 0 0 1-1.119-.813l.76-4.431a.77.77 0 0 0-.222-.683L.233 6.846A.772.772 0 0 1 .661 5.53l4.449-.647a.772.772 0 0 0 .58-.422L7.68.43a.774.774 0 0 1 1.387 0Z" fill="#FC7614"/></svg>
      </div>

      <h1>How did we do?</h1>

      <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>

      <form on:submit|preventDefault={handleSubmit}>
        <div class="btn-group">
          <button type="button" on:click={updateRating} class:selected={rating === 1}>1</button>
          <button type="button" on:click={updateRating} class:selected={rating === 2}>2</button>
          <button type="button" on:click={updateRating} class:selected={rating === 3}>3</button>
          <button type="button" on:click={updateRating} class:selected={rating === 4}>4</button>
          <button type="button" on:click={updateRating} class:selected={rating === 5}>5</button>
        </div>

        <button type="submit" class="btn-primary">Submit</button>
      </form>
    </div>
  {:else}
    <div class="card text-center" transition:fade>
      <img src="/illustration-thank-you.svg" alt="" width="162" height="108" class="illustration">

      <p class="badge">You selected {rating} out of 5</p>

      <h1>Thank you!</h1>

      <p class="mb-0">We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!</p>
    </div>
  {/if}
</main>
