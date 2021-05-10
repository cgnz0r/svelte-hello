<script>
    let user = {
        loggedIn: false,
    };
    
    let x = 7;

    const toggle = () => {
        user.loggedIn = !user.loggedIn;
    };
</script>

<h4>Toggle</h4>

{#if user.loggedIn}
    <button on:click={toggle}>Log Out</button>
{:else}
    <button on:click={toggle}> Log In </button>
{/if}

<h4>Input - several if else</h4>

<input type="text" bind:value={x}>

{#if x > 10}
    <p>{x} is greater than 10</p>
{:else if 5 > x}
    <p>{x} is less than 5</p>
{:else if 5 == x || 10 == 10}
    <p>{x} is equal {x}</p>
{:else}
    <p>5 is less than {x} and {x} is less than 10</p>
{/if}