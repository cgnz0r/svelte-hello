<script>
    export let name, age, profession;
</script>

<div class="card-wrapper">
    <div class="card">
        <h4>{name} info:</h4>
        <p>{age} years, {profession}</p>
    </div>
</div>

<style>
    .card-wrapper {
        border: 1px solid #8a8;
        box-shadow: 0px 3px 5px 1px gray;
    }

    .card {
        padding: 10px;
    }

    .card * {
        text-align: left;
    }

    h4 {
        margin: 0;
    }

    h4:after {
        display: none;
    }
</style>
