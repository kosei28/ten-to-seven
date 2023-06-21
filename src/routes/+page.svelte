<script lang="ts">
    let tenNumber = 0n;
    let sevenNumber = 0n;

    function onInput(e: Event) {
        tenNumber = BigInt((e.target as HTMLInputElement).value);
    }

    function convert() {
        let tmp = tenNumber;
        sevenNumber = 0n;
        let i = 0n;
        while (tmp > 0) {
            sevenNumber += 10n ** i * (tmp % 7n);
            tmp = tmp / 7n;
            i += 1n;
        }
    }
</script>

<svelte:head>
    <title>Ten to Seven</title>
</svelte:head>

<h1>10進数を7進数に変換</h1>

<form
    on:submit={(e) => {
        e.preventDefault();
        convert();
    }}
>
    <input type="text" placeholder="10進数を入力" on:input={onInput} />
    <button type="submit">変換</button>
</form>

<div class="result">
    <p>7進数</p>
    <p>{sevenNumber}</p>
</div>

<style>
    :global(body) {
        margin: 16px;
    }
    h1 {
        margin: 0;
        font-size: 1.25rem;
        font-weight: bold;
    }
    form {
        margin-top: 16px;
        display: flex;
    }
    input {
        flex: 1;
        margin-right: 8px;
    }
    .result {
        margin-top: 16px;
        overflow-wrap: break-word;
    }
    .result p {
        margin: 0;
        margin-top: 4px;
    }
</style>
