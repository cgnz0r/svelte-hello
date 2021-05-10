<script>
    let cats = [
        { id: "J---aiyznGQ", name: "Кот на клавишных" },
        { id: "z_AbfPXTKms", name: "Мару" },
        { id: "OUtn3pvWmpg", name: "Экзистенциальный кот" },
    ];

    let things = [
		{ id: 1, color: 'darkblue' },
		{ id: 2, color: 'indigo' },
		{ id: 3, color: 'deeppink' },
		{ id: 4, color: 'salmon' },
		{ id: 5, color: 'gold' }
	];

    function handleClick() {
        things = things.slice(1);
    }
</script>

<h4>YT Cats</h4>

<ul>
    {#each cats as cat, i}
        <li>
            <a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
                {i + 1}: {cat.name}
            </a>
        </li>
    {/each}
</ul>

<!-- or destructured

<ul>
    {#each cats as {id, name}, i}
        <li>
            <a target="_blank" href="https://www.youtube.com/watch?v={id}">
                {i + 1}: {name}
            </a>
        </li>
    {/each}
</ul>

-->

<h4>Keyed each blocks</h4>

{#each things as thing (thing.id)}
    <span style="background-color: {thing.color}">{thing.color}</span>
{/each}

<button on:click={handleClick}>remove first</button>

<style>
    li {
        list-style-type: none;
        text-align: left;
    }

    span {
        display: block;
        color: white;
        padding: 5px;
        margin: 5px;
    }
</style>