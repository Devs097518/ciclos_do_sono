<script lang="ts">
    let a: number = 4; // <--  [   as horas que quer acordar ]
    let b: number = 0; // <--  [  os minutos quer acordar    ]

    let horarios: string[] = [];

    // transforma do teu horario para minutos [ 1h30 -> 90mnt ]
    function horasParaMinutos(b_horas: number, b_minutos: number): number {
        b_horas = b_horas * 60;
        let result = b_horas + b_minutos;
        return result;
    }

    function minutosParaHoras(): void {
        horarios = [];
        // contém os minutos do seu horario
        let horario_extenso = horasParaMinutos(a, b);

        //  [  os 7 momentos ideais de se adormecer ]
        for (let i = 7; i > 0; i--) {
            let h: number = 0;
            let m: number = 0;

            //  [   são os pulos pra os horários ideais   ]
            horario_extenso = horario_extenso - 90;

            if (horario_extenso <= 0) {
                horario_extenso += 1440;
            }

            //  [   converte de minutos extensos para 00h00   ]
            for (let contador = 0; contador < horario_extenso; contador++) {
                m++;
                if (m === 60) {
                    m = 0;
                    h += 1;
                }
                if (h === 24) {
                    h = 0;
                }
            }

            //   [  printa o resultado  ]

            horarios.push(
                `${h.toString().padStart(2, "0")}h${m.toString().padStart(2, "0")}`,
            );
        }
    }
</script>

<div id="container">
    <div id="area1">
        <div id="in-hora">
            <div>
                <p>Qual o horário do alarme?</p>
            </div>
            <div id="in-num">
                <div>
                    <input
                        class="receber"
                        type="number"
                        min="0"
                        max="24"
                        bind:value={a}
                    />
                    <label for="">horas</label>
                </div>
                <div>
                    <input
                        class="receber"
                        type="number"
                        min="0"
                        max="60"
                        bind:value={b}
                    />
                    <label for="">minutos</label>
                </div>
            </div>
        </div>
        <button on:click={minutosParaHoras}
            >Os melhores horários para dormir são:</button
        >
        <ul>
            {#each horarios as w}
                <li>{w}</li>
            {/each}
        </ul>
    </div>
</div>

<style>
    :global(:root) {
        background-image: radial-gradient(#695f9d 1px, #eeebff 1px);
        background-size: 10px 10px;
        font-family: monospace;
        font-size: 12px;
        text-align: center;
    }

    #container {
        display: flex;
        justify-content: center;
    }

    #area1 {
        display: flex;
        flex-direction: column;
        width: 50em;
        justify-content: center;
        background-color: #695f9d;
        padding: 5em;
        border: 1px solid black;
    }

    #in-hora {
        width: 100%;
        height: 10em;
        background-color: rgb(255, 244, 183);
    }

    #in-num {
        display: flex;
        justify-content: space-around;
    }

    .receber {
        width: 3em;
    }

    ul {
        display: flex;
        align-items: center;
        margin: 0;
        flex-direction: column;
        background-color: rgb(255, 244, 183);
    }

    li {
        list-style: none;
        font-size: 1.7em;
        margin: 0.3em;
        border: black solid 1px;
        padding: 10px;
        border-radius: 25px;
    }
</style>
