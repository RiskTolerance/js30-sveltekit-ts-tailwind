<script lang="ts">
	interface Inventor {
		first: string;
		last: string;
		year: number;
		passed: number;
		yearsLived?: number;
	}
	const inventors: Inventor[] = [
		{ first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
		{ first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
		{ first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
		{ first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
		{ first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
		{ first: 'Nicolaus', last: 'Copernicus', year: 1473, passed: 1543 },
		{ first: 'Max', last: 'Planck', year: 1858, passed: 1947 },
		{ first: 'Katherine', last: 'Blodgett', year: 1898, passed: 1979 },
		{ first: 'Ada', last: 'Lovelace', year: 1815, passed: 1852 },
		{ first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
		{ first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
		{ first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
	];

	// Array.prototype.filter()
	// 1. Filter the list of inventors for those who were born in the 1500's

	let fifteenHundreds = inventors.filter((x) => x.year > 1499 && x.year < 1600);
	console.log(fifteenHundreds);

	// Array.prototype.map()
	// 2. Give us an array of the inventors first and last names

	async function getFirstLast(inventors: Inventor[]) {
		let firstLast: Array<Object> = [];
		inventors.map((x) => firstLast.push({ first: x.first, last: x.last }));
		return firstLast;
	}

	interface FullNames {
		[key: string]: any;
	}
	let firstLast: Promise<FullNames[]> = getFirstLast(inventors);

	// Array.prototype.sort()
	// 3. Sort the inventors by birthdate, oldest to youngest

	let sortedBirth: Inventor[] = inventors.sort((a, b) => {
		return a.year > b.year ? 1 : -1;
	});

	// Array.prototype.reduce()
	// 4. How many years did all the inventors live all together?

	let totalYears = inventors.reduce(
		(accum, investor) => accum + (investor.passed - investor.year),
		0
	);

	// 5. Sort the inventors by years lived

	async function lifespan(inventors: Inventor[]) {
		inventors.forEach((inventor) => {
			inventor.yearsLived = inventor.passed - inventor.year;
		});
		inventors.sort((a, b) => {
			if (a.yearsLived && b.yearsLived) {
				return a.yearsLived - b.yearsLived;
			}
			return 0;
		});
		return inventors;
	}

	let investorLifespan: Promise<Inventor[]> = lifespan(inventors);

	// 6. create a list of Boulevards in Paris that contain 'de' anywhere in the name
	// https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris

	const franceBlvds = [
		'Boulevards of Paris',
		'City walls of Paris',
		'Thiers wall',
		'Wall of Charles V',
		'Wall of Philip II Augustus',
		'City gates of Paris',
		"Haussmann's renovation of Paris",
		'Boulevards of the Marshals',
		'Boulevard Auguste-Blanqui',
		'Boulevard Barbès',
		'Boulevard Beaumarchais',
		"Boulevard de l'Amiral-Bruix",
		'Boulevard Mortier',
		'Boulevard Poniatowski',
		'Boulevard Soult',
		'Boulevard des Capucines',
		'Boulevard de la Chapelle',
		'Boulevard de Clichy',
		'Boulevard du Crime',
		"Boulevard du Général-d'Armée-Jean-Simon",
		'Boulevard Haussmann',
		"Boulevard de l'Hôpital",
		'Boulevard des Italiens',
		'Boulevard Lefebvre',
		'Boulevard de la Madeleine',
		'Boulevard de Magenta',
		'Boulevard Malesherbes',
		'Boulevard Marguerite-de-Rochechouart',
		'Boulevard Montmartre',
		'Boulevard du Montparnasse',
		'Boulevard Raspail',
		'Boulevard Richard-Lenoir',
		'Boulevard Saint-Germain',
		'Boulevard Saint-Michel',
		'Boulevard de Sébastopol',
		'Boulevard de Strasbourg',
		'Boulevard du Temple',
		'Boulevard Voltaire',
		'Boulevard de la Zone'
	];

	async function deCheck(franceBlvds: string[]) {
		let matches: string[] = [];
		franceBlvds.forEach((blvd) => {
			if (blvd.match(/de/i)) {
				matches.push(blvd);
			}
		});
		return matches;
	}

	let deFranceBlvds: Promise<string[]> = deCheck(franceBlvds);

	// 7. sort Exercise
	// Sort the people alphabetically by last name

	const people = [
		'Bernhard, Sandra',
		'Bethea, Erin',
		'Becker, Carl',
		'Bentsen, Lloyd',
		'Beckett, Samuel',
		'Blake, William',
		'Berger, Ric',
		'Beddoes, Mick',
		'Beethoven, Ludwig',
		'Belloc, Hilaire',
		'Begin, Menachem',
		'Bellow, Saul',
		'Benchley, Robert',
		'Blair, Robert',
		'Benenson, Peter',
		'Benjamin, Walter',
		'Berlin, Irving',
		'Benn, Tony',
		'Benson, Leana',
		'Bent, Silas',
		'Berle, Milton',
		'Berry, Halle',
		'Biko, Steve',
		'Beck, Glenn',
		'Bergman, Ingmar',
		'Black, Elk',
		'Berio, Luciano',
		'Berne, Eric',
		'Berra, Yogi',
		'Berry, Wendell',
		'Bevan, Aneurin',
		'Ben-Gurion, David',
		'Bevel, Ken',
		'Biden, Joseph',
		'Bennington, Chester',
		'Bierce, Ambrose',
		'Billings, Josh',
		'Birrell, Augustine',
		'Blair, Tony',
		'Beecher, Henry',
		'Biondo, Frank'
	];

	let sortedNames: String[] = people.sort((a, b) => {
		let aLast = a.split(', ')[0];
		let bLast = b.split(', ')[0];
		return aLast > bLast ? 1 : -1;
	});

	// 8. Reduce Exercise
	// Sum up the instances of each of these
	const data = [
		'car',
		'car',
		'truck',
		'truck',
		'bike',
		'walk',
		'car',
		'van',
		'bike',
		'walk',
		'car',
		'van',
		'car',
		'truck'
	];

	const transport = data.reduce((vehicles: { [key: string]: number }, vehicle) => {
		const currCount = vehicles[vehicle] ?? 0;
		return {
			...vehicles,
			[vehicle]: currCount + 1
		};
	}, {});
	console.log(transport);
</script>

<div class="flex flex-col">
	<h2 class="font-bold">Filter the list of inventors for those who were born in the 1500's:</h2>

	{#each fifteenHundreds as item}
		<p>{item.first} {item.last}, {item.year}</p>
	{/each}

	<h2 class="font-bold">Print an array of the inventors first and last names:</h2>

	{#await firstLast then items}
		{#each items as item}
			<p>{item.first} {item.last}</p>
		{/each}
	{/await}

	<h2 class="font-bold">Sort the inventors by birthdate, oldest to youngest:</h2>

	{#each sortedBirth as item}
		<p>{item.first} {item.last}, {item.year}</p>
	{/each}

	<h2 class="font-bold">How many years did the inventors live in total?</h2>

	<p>{totalYears}</p>

	<h2 class="font-bold">Sort the inventors by years lived:</h2>
	{#await investorLifespan then values}
		{#each values as value}
			<p>{value.first} {value.last}, {value.yearsLived}</p>
		{/each}
	{/await}

	<h2 class="font-bold">
		List all the Boulevards in Paris that contain 'de' anywhere in the name.
	</h2>

	{#await deFranceBlvds then values}
		{#each values as value}
			<p>{value}</p>
		{/each}
	{/await}

	<h2 class="font-bold">Sort the people by their last name:</h2>

	{#each sortedNames as item}
		<p>{item}</p>
	{/each}

	<h2 class="font-bold">Sum the instances of the vehicles:</h2>
	{#each Object.entries(transport) as [key, value]}
		<p>{key}: {value}</p>
	{/each}
</div>
