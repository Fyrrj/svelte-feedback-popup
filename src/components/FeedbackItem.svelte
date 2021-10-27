<script>
    import {createEventDispatcher} from 'svelte';
    import Card from "./Card.svelte";
    export let item;

    const dispatch = createEventDispatcher();

    const handleDelete = (itemId) => {
        dispatch('delete-fedback', itemId)
    }

</script>

<Card>
<div class="num-display">
    {item.rating}
</div>
<button class="close" on:click={() => handleDelete(item.id)}>
    <i class="fas fa-window-close"></i>
</button>
<div class="text-display">
    {item.text}
</div>
</Card>

<style>
    .num-display {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: -25px;
        left: -25px;
        width: 50px;
        height: 50px;
        background: #ff6a95;
        color: #fff;
        border: 2px solid #eee;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 20px;
    }
    .close {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        color: #ff6a95;
        font-size: 1.4rem;
        opacity: 0.5;
        transition: .2s;
        background: none;
        border: none;
    }
    .close:hover {
        opacity: 1;
    }
</style>