

<script lang="ts">
    import CryptoJS from "crypto-js";
    import axios from "axios";
    import { onMount } from 'svelte';
    //import assets
    import OkBearGif from '../assets/bear-kiss-bear-kisses.gif'
    //import data
    import {ok} from '../Data/settings.json'

    export let name: string

    type queryParamType = string | null
    

    
    onMount(async () => {
        const queryString:string = window.location.search;
        const urlParams = new URLSearchParams(queryString)
        
        // Pobierz wartość parametru 'q'
        const quantityParam:queryParamType = urlParams.get('q');
        // Pobierz wartość parametru 'uid'
        name = urlParams.get('uid');
        
        if(name){
            const nameDecoded = CryptoJS.AES.decrypt(decodeURIComponent(name), import.meta.env.VITE_SECRET_KEY).toString(CryptoJS.enc.Utf8);
            axios.post(`https://api.telegram.org/bot${import.meta.env.VITE_TELEGRAM_BOT_TOKKEN}/sendMessage`, {
                chat_id: import.meta.env.VITE_TELEGRAM_USER_ID,
                text:   `Nacisła nie: ${quantityParam} razy.... Ale w końcu powiedziała tak! - ${nameDecoded} `
            });

        }
    });
</script>

<main>
    <img src="{OkBearGif}" alt="Final bear">
    <h2>{ok.title}</h2>
</main>