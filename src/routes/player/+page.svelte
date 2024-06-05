<script>
    import { PUBLIC_BASE_URL } from '$env/static/public';
 	import axios from "axios";

	let fifa_rating;
	let age;
	let appearance;

	
	let current_value = '...'
	let selected;
	function handleSubmit() {
		let url =
            PUBLIC_BASE_URL +
            "/api/prediction/player?appearance=" +
            selected.id +
            "&age=" +
            age +
            "&fifa_rating=" +
            fifa_rating;
        console.log(url);
        axios.get(url).then((response) => {
            current_value = 'EUR ' + response.data;
        });
	}
</script>
<div class="container text-center">

	<h1>Whats the market value of your player? {current_value}</h1>

	<div class="row justify-content-md-center">
	  <div class="col col-lg-2">
        <input type="number" class="form-control" placeholder="age" aria-label="age" bind:value={age} min="16" max="45">
	  </div>

	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="fifa_rating" aria-label="fifa_rating" bind:value={fifa_rating}>
	  </div>

	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="appearance" aria-label="appearance" bind:value={appearance}>
	  </div>

	  <div class="col-md-auto">
		<button type="button" class="btn btn-primary" on:click={handleSubmit}>value estimation</button>
	  </div>
	</div>
  </div>