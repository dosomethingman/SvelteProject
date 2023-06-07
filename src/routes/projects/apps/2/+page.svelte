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
    function deleteExpence (index) {
        costs.splice(index, 1);
        costs = costs;
    }
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
                    <td><button class="delete-cost" on:click={() => deleteExpence(index)}>Удалить</button></td>
                </tr>
            {/each}
        </tbody>
    </table>

</main> 
    
<style>
    .cost-form, td {
        background-color: rgb(250, 250, 250);
        box-shadow: 5px 4px 3px lightgray;
        border: 1px solid magenta;
        color: navy;
    }
    td {
        padding: 5px;
    }
    .cost-form {
        display: flex;
        justify-content: space-around;
        padding: 5px;
        width: 100%;
    }
    .costs-table {
        width: 100%;
        margin-top: 25px;
    }
    .add-cost, .delete-cost {
        appearance: none;
        border: none;
        padding: 0;
        font-size: 22px;
        color: navy;
        background-color: transparent;
        cursor: pointer;
    }
    .delete-cost {
        font-size: unset;
        color: red;
    }
</style>
