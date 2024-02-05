<script setup>
import Swal from 'sweetalert2'
</script>

<template>
    <div style="display: flex; flex-direction: column; align-items: center; text-align: center; margin: auto;">
        <h1>¿Quieres salir conmigo en San Valentín?</h1>
        <div style="width: 1px; height: 30px"></div>
        <div class="contenedor">
            <BButton variant="primary" :style="btnSiStyle" ref="btnSi" @click="si_pressed">Obvio pues 😊</BButton>
            <div class="separador-hor"></div>
            <BButton variant="danger" style="width: 150px; height: 70px;" ref="btnNo" @click="no_pressed">{{ textosNo[i] }}</BButton>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            btnSiStyle: {
                width: 150 + 'px',
                height: 70 + 'px',
                fontSize: 15 + 'px'
            },
            textosNo: [
                'No gracias 💔',
                'Se que quieres 😏',
                'No seas timida 😉',
                'Lo vas a pasar bien 😊',
                'Comerás cosas ricas 😋',
                'Será una buena cita 👀',
                'Aprovechame 🫢',
                'Te doy otra oportunidad 😣',
                'Me rompes el corazón 💔',
                'Yo invito 😁',
                'Te saco las fotos que quieras 🫡',
                'Nos reiremos harto 🤣',
                'Jugaremos ajedrez 🤓'
            ],
            posTextosNoUsados: [],
            i: 0
        }
    },
    methods: {
        si_pressed() {
            Swal.fire({
                title: "Perfecto!!!",
                html: '<span>Nos vemos en el Starbucks de libertad?<br>O en el café que quieras 😉</span>',
                icon: "success"
            });
        },
        no_pressed() {
            this.posTextosNoUsados.push(this.i)
            if (this.textosNo.length > this.posTextosNoUsados.length) {
                let ran
                do {
                    ran = Math.floor(Math.random() * this.textosNo.length)
                } while(this.posTextosNoUsados.includes(ran))
                this.i = ran
                this.btnSiStyle.width = (parseInt(this.btnSiStyle.width.substring(0, this.btnSiStyle.width.length - 2)) + 50) + 'px'
                this.btnSiStyle.height = (parseInt(this.btnSiStyle.height.substring(0, this.btnSiStyle.height.length - 2)) + 30) + 'px'
                this.btnSiStyle.fontSize = (parseInt(this.btnSiStyle.fontSize.substring(0, this.btnSiStyle.fontSize.length - 2)) + 7) + 'px'
            } else {
                Swal.fire({
                    title: "AAAAAAAAAAAAAAAAAA",
                    html: '<span>Se me acabaron las frases 🤧<br>Dale, acepta 🥺</span>',
                    icon: "warning"
                });
            }
        }
    }
}
</script>

<style scoped>
@media (min-width: 1024px) {
    .separador-hor {
        width: 50px;
        height: 1px;
    }

    .contenedor {
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
}

@media (max-width: 1024px) {
    .separador-hor {
        width: 0px;
        height: 0px;
    }

    .contenedor {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
}
</style>