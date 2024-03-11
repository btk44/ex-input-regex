<script>
    import { accounts, categories, currencies } from './data'

    let selectedAccount
    let selectedCategory
    let selectedSubcategory

    let amount = 0
    let payee = ''
    let comment = ''
    let currentInput = ''

    let processInput = () => {
        let values = currentInput.split(' ');
        if(values && !isNaN(values[0])){ selectedAccount = +values[0] }
        if(values && !isNaN(values[1])){ amount = +values[1] }
        if(values && values[2]){ payee = values[2] }
        if(values && !isNaN(values[3])){ selectedCategory = +values[3] }
        if(values && !isNaN(values[4])){ selectedSubcategory = +values[4] }
        if(values && values[5]){ comment = values[5] }
    }
</script>

<input type="date" value="{ new Date().toISOString().split('T')[0] }"/>
<select id="account" bind:value={selectedAccount}>
    {#each accounts as account}
    <option value={account.id}>
        {account.id} - {account.name}
    </option>
    {/each}
</select>
<input type="text" bind:value={amount}/>
<input type="text" bind:value={payee}/>
<select id="category" bind:value={selectedCategory}>
    {#each categories as category}
    <option value={category.id}>
        {category.id} - {category.name}
    </option>
    {/each}
</select>
<select id="subcategory" bind:value={selectedSubcategory}>
    {#each categories as subcategory}
    <option value={subcategory.id}>
        {subcategory.id} - {subcategory.name}
    </option>
    {/each}
</select>
<input type="text" bind:value={comment}/>
<br><br><br>
<input type="text" bind:value={currentInput} on:keyup={processInput}/>
<button>OK</button>
<style>
    input { display: block; margin: 2px; }

</style>