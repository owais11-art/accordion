<script setup>
    import { ref } from 'vue'
    import { data } from '../data/siteData'
    import Faq from './Faq.vue'

    const faqs = ref(data)

    const toggleAnswer = id => {
        faqs.value = faqs.value.map(faq => faq.isOpen && faq.id !== id ? {...faq, isOpen: false} : faq)
                               .map(faq => faq.id === id ? {...faq, isOpen: !faq.isOpen} : faq)
    }
</script>

<template>
    <main>
        <div class="faqs">
            <Faq
                v-for="faq in faqs"
                :key="faq.id"
                :faq="faq"
                @toggle-answer="toggleAnswer"
            />
        </div>
    </main>
</template>

<style scoped lang="less">
    main{
        width: 500px;
        box-shadow: 5px 5px 20px 0 rgba(0, 0, 0, 0.5);
        margin: 0 auto;
        margin-top: 10%;
        margin-bottom: 10%;
        background-color: rgb(240, 248, 255);
        padding: 10px;
        border-radius: 6px;
        .faqs{
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
    }
</style>