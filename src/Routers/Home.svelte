<script lang="ts">
    import { Link } from "svelte-routing";
    import { onMount } from 'svelte';
    //import assets
    import LoveBear from "../assets/LoveBear.gif";
    import {home, ok} from "../Data/settings.json";
    //import style
    import "../Style/Views/Home.css";

    let uid:string;
    let adminToken:string;
    let isAdmin:boolean

    onMount(() => {
        const searchParams = new URLSearchParams(window.location.search);
        uid = searchParams.get('uid');
        if(searchParams.get('admin_token') == import.meta.env.VITE_ADMIN_TOKEN){
            isAdmin=true;
        }
        else{
            isAdmin=false
        }

    });

    let fontSize: number = 1;

    type IncreaseFontSizeType = ()=> Number
    type ReturnTitleToNoButtonType = (index: number) => String

    const increaseFont: IncreaseFontSizeType = () => ++fontSize;

    const showTitleToButtonNo:ReturnTitleToNoButtonType = index => home.changeNo[(index % home.changeNo.length)]

</script>

<main>
    <img src="{LoveBear}" alt="Loved bear">
    <h2>{home.title}</h2>
    <div class="button">
        <Link class="button__item button__item--yes" to={`/${ok.url}${uid ? '?uid='+uid+'&q='+(fontSize-1) : '?q='+(fontSize-1)}`} style="font-size: {fontSize }em">Tak</Link>
        <button class="button__item button__item--no" on:click={increaseFont}>{showTitleToButtonNo(fontSize - 1)}</button>
    </div>

    {#if isAdmin}
        <Link class="button__item button__item--admin" to={'/admin'}>Admin</Link>
    {/if}
</main>