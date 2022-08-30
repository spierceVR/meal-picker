<script lang="ts">
	export let name: string;
	export let foodData: object;


	const fetchFoodData = async () => {
		const options = {
			method: "GET",
			headers: {
				"X-RapidAPI-Key":
					"7bb2e9d73fmsh5dda51740d209eap1731eejsnce261f4468c8",
				"X-RapidAPI-Host": "themealdb.p.rapidapi.com",
			},
		};
		
		let API_response = fetch(
			"https://themealdb.p.rapidapi.com/filter.php?i=chicken_breast",
			options
		);
		 
		return API_response;
	};

	const onClick = async (e) => {
		foodData = await fetchFoodData();
	};
</script>

<main>
	<h1>Hi {name}, welcome to Meal Picker!</h1>
	<button on:click={onClick}>Click to get a meal suggestion!</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
