<script setup>
    import chev from '../assets/chev.svg'
    defineProps(['faq'])
    const emit = defineEmits(['toggleAnswer'])
    const handleClick = id => emit('toggleAnswer', id)
</script>

<template>
    <div class="faq">
        <div class="header" @click="() => handleClick(faq.id)">
            <div class="question">{{ faq.question }}</div>
            <div :class="['icon', {open: faq.isOpen}]">
                <img :src="chev" alt="chevron">
            </div>
        </div>
        <div :class="['answer', {open: faq.isOpen}]">
            <p>{{ faq.answer }}</p>
        </div>
    </div>
</template>

<style scoped lang="less">
   .faq{
    flex-grow: 1;
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        border: 2px solid antiquewhite;
        padding: 10px;
        border-radius: 6px 6px 0 0;
        cursor: pointer;
        .question{
            font-weight: 700;
        }
        .icon{
            width: 30px;
            height: 30px;
            transition: transform .5s;
            img{
                width: 100%;
                height: auto;
            }
            &.open{
                transform: rotate(180deg);
            }
        }
    }
    .answer{
        height: 0;
        overflow-y: scroll;
        line-height: 1.5;
        background-color: antiquewhite;
        transition: height .5s;
        &::-webkit-scrollbar{
            width: 5px;
        }
        &::-webkit-scrollbar-track{
            appearance: none;
            background-color: transparent;
        }
        &::-webkit-scrollbar-thumb{
            width: 5px;
            background-color: rgb(232, 210, 182);
            border-radius: 50px;
        }
        p{
            padding: 10px;
        }
        &.open{
            height: 200px;
        }
    }
   }
</style>