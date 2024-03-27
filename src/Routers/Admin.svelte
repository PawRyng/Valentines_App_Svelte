<script lang="ts">
    import { admin } from "../Data/settings.json"
    import CryptoJS  from "crypto-js";
    import '../Style/Views/Admin.css'
    type stringFunctionType = (event: string) => string;

    let name: String = "";
    let link: string = "";
    let coppy: Boolean = false;

    const onChangeHandler: stringFunctionType = e => name = e.target.value;
    
    
    const generateLink = ()=>{
        const encrypted: string = CryptoJS.AES.encrypt(name, import.meta.env.VITE_SECRET_KEY).toString();
        link = `${window.location.host}?uid=${encodeURIComponent(encrypted)}`
    } 

const coppyHandler = e => {
    navigator.clipboard.writeText(link);
    coppy = true;
}
</script>


<main>
    <h2>{admin.title}</h2>
    <div class="button">
        <input type="text" name="name" placeholder="imię" id="name" on:input={onChangeHandler}>

        {#if name}
            <button class="button__item button__item--yes" on:click={generateLink} >Generuj</button>
        {:else}
            <button class="button__item button__item--yes" disabled >Generuj</button>
        {/if}
    </div>
    {#if link}
        <p class="link"><span>{link}</span><button on:click|once={coppyHandler}>
            <svg id='Copy_24' width='24' height='24' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'><rect width='24' height='24' stroke='none' fill='#000000' opacity='0'/>
            <g transform="matrix(1 0 0 1 12 12)" >
            <path style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-dashoffset: 0; stroke-linejoin: miter; stroke-miterlimit: 4; fill: {coppy ? "#34bf3e" : "#000"}; fill-rule: nonzero; opacity: 1;" transform=" translate(-12, -12)" d="M 4 2 C 2.895 2 2 2.895 2 4 L 2 18 L 4 18 L 4 4 L 18 4 L 18 2 L 4 2 z M 8 6 C 6.895 6 6 6.895 6 8 L 6 20 C 6 21.105 6.895 22 8 22 L 20 22 C 21.105 22 22 21.105 22 20 L 22 8 C 22 6.895 21.105 6 20 6 L 8 6 z M 8 8 L 20 8 L 20 20 L 8 20 L 8 8 z" stroke-linecap="round" />
            </g>
            </svg></button></p>
    {/if}
</main>