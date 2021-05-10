<script>
    async function getRandomNumber() {
        const res = await fetch(`https://svelte.dev/tutorial/random-number`);
        const text = await res.text();

        if (res.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }

    let promise = getRandomNumber();

    function handleClick() {
        promise = getRandomNumber();
    }
</script>

<div class="await-section">
    {#await promise}
        <p>Please wait...</p>
    {:then number}
        <p class="result">The number is {number}</p>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
</div>

<div class="await-section">
    <p style="color: #bbb">Or brutally, w/o messages</p>

    {#await promise then value}
        <p class="result">The number is {value}</p>
    {/await}
</div>

<button on:click={handleClick}>Get random number</button>

<style lang="scss">
    .await-section {
        border: 1px solid gray;
        margin: 5px 0;

        &:before {
            content: "await-section";
            font-size: 10px;
        }
    }

    .result {
        text-decoration: underline;
    }
</style>
