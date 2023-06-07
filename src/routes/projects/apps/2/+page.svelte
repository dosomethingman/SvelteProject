<svelte:head>
    <title>Учёт расходов</title>
</svelte:head>

<script>
    let costs = [];
    let newCost = {};

    function addExpence () {
        if (newCost.summ < 0) {
            newCost.summ *= -1;
        }
        costs = [
            ...costs,
            {
                name: newCost.name,
                summ: newCost.summ,
                dateAdded: newCost.dateAdded,
            },
        ]
        newCost = {};
    };
</script>

<main>

    <h1>Учёт расходов</h1>

    <form class="cost-form" on:submit|preventDefault={addExpence}>

        <div class="input-field">
            <label for="name">Название</label>
            <input type="text" id="name" class="form-element" cols=20 required bind:value={newCost.name}>
        </div>

        <div class="input-field">
            <label for="summ">Сумма</label>
            <input type="number" id="summ" class="form-element" cols=20 required bind:value={newCost.summ}>
        </div>

        <div class="input-field">
            <label for="date-added">Дата</label>
            <input type="date" id="date-added" class="form-element" cols=20 bind:value={newCost.dateAdded}>
        </div>

        <button class="add-cost">+</button>
    </form>

    <table class="costs-table">
        <thead>
            <tr class="table-headers">
                <td>Название</td>
                <td>Сумма</td>
                <td>Дата</td>
                <td>Действия</td>
            </tr>
        </thead>
        <tbody>
            {#each costs as cost, index}
                <tr>
                    <td>{cost.name}</td>
                    <td>{cost.summ}</td>
                    {#if cost.dateAdded}
                        <td>{cost.dateAdded}</td>
                    {:else}
                        <td>Не указана</td>
                    {/if}
                    <td>Действия</td>
                </tr>
            {/each}
        </tbody>
    </table>

</main> 
    
<style>
    .cost-form, .costs-table {
        border: 2px solid magenta;
        box-shadow: 5px 4px 3px lightgray;
        color: navy;
    }
    td {
        border: 1px solid lightgray;
    }
    .cost-form {
        display: flex;
        justify-content: space-between;
        padding: 15px;
    }
    .costs-table {
        width: 100%;
        margin-top: 25px;
        padding: 10px;
    }
    .add-cost {
        appearance: none;
        border: none;
        padding: 0;
        font-size: 22px;
        color: navy;
        background-color: transparent;
    }
</style>
