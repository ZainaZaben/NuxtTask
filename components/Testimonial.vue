<template>
    <div class="testimonials">
        <div class="testimonial" v-for="testimonial in testimonials" :key="testimonial.id">
            <div class="quote">
                <blockquote>
                    <p>{{ testimonial.text }} <span class="read-more">čítať viac</span></p>
                </blockquote>
            </div>
        </div>
    </div>
</template>

<script setup>
const testimonials = [
    {
        id: 1,
        text: 'Pravidelné UX audity a postupné vylepšovanie nášho internetového obchodu je už niekoľko rokov súčasťou našej dlhodobej stratégie v predaji. UX tím v Riešeniach odvádza skvelú prácu, ktorú sprevádzajú viditeľné výsledky a spokojnosť našich zákazníkov. Okrem ich prístupu k nášmu biznisu ...'
    },
    {
        id: 2,
        text: 'S UX tímom Riešení úzko spolupracujeme už dlhé roky a sú dôležitým partnerom nášho biznisu. Vďaka ich know-how pre nás od samého začiatku správne nastavili zdravý pomer prvotriedneho dizajnu a funkčnosti webu, ktorý následne vylepšovali pomocou relevantných analýz a dát. Aj ich zásluhou ...'
    }
];
</script>
