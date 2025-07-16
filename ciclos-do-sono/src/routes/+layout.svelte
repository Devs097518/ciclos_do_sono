<script>
    import { goto } from "$app/navigation";
    import { page } from "$app/stores";
    let selected = "op1";

    $: {
        if (selected == "op2" && $page.url.pathname !== "/soneca") {
            goto("/soneca");
        }
        else if (selected == "op1" && $page.url.pathname !== "/") {
            goto("/");
        }
    }
</script>

<div id="container">
    <div id="topo">
        <div id="banner">
            <img src="img.png" alt="" />
        </div>
        <div id="info">
            <p style="color: rgba(255, 242, 168, 0.822);">
                O corpo passa por vários ciclos de sono durante uma noite, sendo
                que o primeiro dura cerca de 90 minutos e depois a duração vai
                aumentando, até uma média de 100 minutos por ciclo. Um adulto
                geralmente tem entre 4 a 5 ciclos de sono por noite, o que acaba
                por fazer as 8 horas de sono necessárias.
            </p>
        </div>
    </div>
    <div id="options">
        <div>
            <input
                id="op1"
                value="op1"
                type="radio"
                name="ooo"
                bind:group={selected}
            />
            <label for="op1">Primeira opção</label>
        </div>

        <div>
            <input
                id="op2"
                value="op2"
                type="radio"
                name="ooo"
                bind:group={selected}
            />
            <label for="op2">Segunda opção</label>
        </div>
    </div>
</div>

<slot />

<style>
    #container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin: 0;
    }

    #topo {
        display: flex;
        width: 50em;
        justify-content: center;
        background-color: #695f9d;
        padding: 5em;
        margin: auto;
        border: 1px solid black;
    }

    #banner {
        display: flex;
        flex-direction: column;
        width: 50%;
        justify-content: center;
        padding: 1em;
    }

    #info {
        display: flex;
        flex-direction: column;
        width: 50%;
        justify-content: center;
        padding: 1em;
    }

    #options {
        margin: auto;
        display: flex;
        align-items: center;
        width: 60em;
        justify-content: space-around;
        border: 1px solid rgb(255, 220, 123);
        background-color: rgba(255, 242, 168, 0.822);
    }
</style>
