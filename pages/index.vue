<template>
    <div class="wrapper">
        <header>
            <nav>
                <div class="nav-left">
                    <img src="assets/images/logo.png" alt="Logo" class="logo">
                </div>

                <div class="nav-right">
                    <Button buttonClass="cta-button" @click="showPopup">Mám záujem o UX audit</Button>
                </div>
            </nav>
            <div class="nav-center">
                <p class="nav-text">Zvýšte svoje zisky optimalizáciou vášho eshopu.</p>
            </div>
        </header>


        <main>
            <div class="container">

                <div class="first-section">
                    <div class="left-section">
                        <h1>Rýchle <span class="highlight">výsledky</span><br>pomocou UX auditu.</h1>
                        <p>
                            UX auditom vášho riešenia lepšie pochopíte, ako vaši zákazníci používajú váš produkt,
                            <strong>zvýšite ich spokojnosť a hlavne vaše zisky.</strong>
                        </p>
                    </div>
                    <div class="right-section">
                        <div class="partner-logos">
                            <img src="assets/images/googlePartner.png" alt="Google Partner">
                            <img src="assets/images/ADMA.jpg" alt="Member of ADMA">
                        </div>
                        <ListItems :items="benefitsList" />
                    </div>
                </div>


                <div class="call-to-action-wrapper">
                    <div class="call-to-action-text">
                        <p>Dosiahnite lepšie výsledky vašej webstránky alebo e-shopu <strong>pomocou UX auditu.</strong>
                        </p>
                    </div>
                    <div class="nav-right">
                        <button class="call-to-action-button">Mám záujem o UX audit</button>
                    </div>
                </div>

                <Testimonial />

                <TestimonialAuthor :authors="authorsData" />


                <div class="text-wrapper">
                    <h1>Rýchla a jednoduchá<br>cesta k <span class="highlight">výsledkom.</span></h1>
                </div>

                <ProcessTable :steps="stepsData" />
                <div class="heading-container">
                    <h1>Zameriame sa na to<br><span class="highlight">najdôležitejšie.</span></h1>
                </div>

                <div class="final-section">
                    <div class="content-section">
                        <p>Dosiahnite lepšie výsledky vašej webstránky alebo e-shopu<br>
                            <strong>pomocou UX auditu.</strong>
                        </p>
                        <Button buttonClass="cta-button">Mám záujem o UX audit</Button>
                    </div>

                    <div class="features-section">
                        <ListItems :items="featuresList" />
                    </div>
                </div>


            </div>
        </main>



        <footer>
            <div class="footer-section footer-question">
                <pre class="question-text">Máte otázky? Jednoducho </pre>
                <pre class="question-text">sa spýtajte.</pre>
            </div>
            <div class="footer-section">
                <div class="contact-info">
                    <a href="tel:+4210255565726" class="phone">+421 (02) 555 65 726</a>
                    <pre>   </pre>
                    <a href="mailto:uxdesign@riesenia.com" class="email">uxdesign@riesenia.com</a>
                </div>
            </div>
            <div class="footer-section">
                <img src="assets/images/riesenia.png" class="footer-image">
            </div>
        </footer>

        <div v-if="isPopupVisible" class="popup-overlay">
            <div class="popup-content">
                <button class="close-button" @click="closePopup">
                    <img src="assets/images/close.png" alt="Close">
                </button>
                <h2>Jednoducho nám napíšte<br> a my sa vám ozveme.</h2>
                <FormComponent :form="form" :errorMessage="errorMessage" :successMessage="successMessage"
                    buttonClass="cta-button" submitText="Kontaktujte ma" @submit="submitForm" />
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import ListItems from '@/components/ListItems.vue';
import TestimonialAuthor from '~/components/TestimonialAuthor.vue';
import ProcessTable from '~/components/ProcessTable.vue';
import JozefKormanImg from '~/assets/images/JozefKorman.png';
import RichardWohlsteinImg from '~/assets/images/RichardWohlstein.png';
import Arrow1Img from '~/assets/images/arrow1.png';
import Arrow2Img from '~/assets/images/arrow2.png';
import Num1Img from '~/assets/images/1.png';
import Num2Img from '~/assets/images/2.png';
import Num3Img from '~/assets/images/3.png';
import Num4Img from '~/assets/images/4.png';

const isPopupVisible = ref(false);
const submitCount = ref(0);

const form = ref({
    name: '',
    email: '',
    phone: '',
    website: '',
    note: ''
});

const errorMessage = ref('');
const successMessage = ref('');

const benefitsList = [
    'Odhalíme nedostatky na vašej stránke',
    'Zvýšime konverzný pomer vašich stránok',
    'Zvýšime výkon marketingových kampaní',
    'Znížime vaše náklady na vývoj',
    'Zvýšime návštevnosť vašich stránok'
];

const featuresList = [
    'Informačnú architektúru a štruktúru kategórií',
    'Správanie návštevníkov na kľúčových stránkach',
    'Rýchlosť a dostupnosť stránok, SEO nastavenia',
    'Váš biznis a vašich zákazníkov',
    'Ciele, ktoré chcete dosiahnuť',
    'Webovú analytiku'
]

const authorsData = [
    {
        name: 'Jozef Korman',
        title: 'Konateľ',
        company: 'SvetNápojov.sk',
        pic: JozefKormanImg
    },
    {
        name: 'Richard Wohlstein',
        title: 'Retail manager',
        company: 'AlainDelon.sk',
        pic: RichardWohlsteinImg
    }
];

const stepsData = [
    {
        numberImage: Num1Img,
        title: 'Ciele auditu',
        description: `Určíme si <strong>spoločné ciele</strong>, nastavíme očakávania <br> a definujeme
                  <strong>cieľovú skupinu a jej potreby.</strong>`,
        arrow: Arrow1Img
    },
    {
        numberImage: Num2Img,
        title: 'Zbieranie dát',
        description: `Zvolíme vhodné metodiky a nástroje na <strong>sledovanie <br> správania používateľov a zbieranie dát.</strong>`,
        arrow: Arrow2Img
    },
    {
        numberImage: Num3Img,
        title: 'Vyhodnotenie',
        description: `<strong>Vyhodnotíme nazbierané dáta</strong>, zosumarizujeme <br> všetky naše zistenia a <strong>navrhneme riešenia.</strong>`,
        arrow: Arrow1Img
    },
    {
        numberImage: Num4Img,
        title: 'Výsledky auditu',
        description: `Osobná prezentácia výsledkov a navrhnutých <br> riešení s podrobnou dokumentáciou.`,

    }
];

const showPopup = () => {
    isPopupVisible.value = true;
};

const closePopup = () => {
    isPopupVisible.value = false;
    errorMessage.value = '';
    successMessage.value = '';
};

const submitForm = () => {
    if (submitCount.value === 0) {
        errorMessage.value = 'There was an error processing the form. Please try again.';
        successMessage.value = '';
        submitCount.value++;
    } else {
        successMessage.value = 'Your form has been successfully submitted!';
        errorMessage.value = '';
    }
};
</script>