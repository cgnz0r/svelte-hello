<script>
import Eachstatement from "./Eachstatement.svelte";
import Ifstatement from "./Ifstatement.svelte";
import XetNested from "./XetNested.svelte";
import Person from "./Person.svelte";
import Awaited from "./Awaited.svelte";

// counter section 
    export let count = 0;

    // reactive value
    $: doubled = count * 2;
    
    // reactive statement
    $: if (count == 5) alert("It is 5!");

    $: console.log("Count is " + count);

    // or
    // $: {
    //     console.log("Count is " + count);
    //     alert("aaaa");
    // }

    // handler
    const clickHandler = () => {
        ++count;
        console.log(`Value: ${count}; Doubled value: ${doubled}`);
    };

// numbers section
    let numbers = [1, 2, 3, 4];
    const addButtonLabel = "add a number";

    $: sum = numbers.reduce((curr, next) => curr + next, 0);

    const addValueHandler = () => {
        // because number.push(numbers.length + 1) doesn't update the numbers' reactives.
        // pop, shift, unshift, splice also don't work.
        numbers = [...numbers, numbers.length + 1];
    }

// props section
    const answerFromApp = 15;

    const info = {
        name: "John",
        age: 25,
        profession: "Backend developer"
    }
</script>

<main>
    <section>
        <h3>1. Counter</h3>
        <button on:click={clickHandler}>
            {count === 0 ? "Click it!" : `Clicks: ${count}`}
        </button>
    </section>
    <section>
        <h3>2. Numbers</h3>
        <p>{numbers.join(" + ")} = {sum}</p>
        <button on:click={addValueHandler}>{addButtonLabel}</button>
    </section>
    <section>
        <h3>3. Props</h3>
        <XetNested answer={answerFromApp}/>
        <XetNested />
        <Person {...info} />
    </section>
    <section>
        <h3>4. If statement</h3>
        <Ifstatement />
    </section>
    <section>
        <h3>5. Each statement</h3>
        <Eachstatement />
    </section>
    <section>
        <h3>5. Async await</h3>
        <Awaited />
    </section>
</main>

<style>
    section {
        border-bottom: 1px solid rgb(212, 212, 212);
        padding-bottom: 10px;
    }

    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }
    
    h3 {
        text-align: left;
    }

    :global(h4) {
        text-align: left;
        overflow: hidden;
    }

    :global(h4:after) {
        content:"";
        display: inline-block;
        height: 0.5em;
        vertical-align: bottom;
        width: 100%;
        margin-right: -100%;
        margin-left: 10px;
        border-top: 1px solid black;
    }

    :global(button) {
        width: 100%;
        height: 40px;
        box-sizing: border-box;
    }
</style>
