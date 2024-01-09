<template>
    <div class="mb-3">
        <input v-model="data.name" class="form-control"/>
    </div>
    <button class="btn btn-primary" @click="addOne">
        Add user
    </button>
    <hr/>
    <div>
        <ul class="list-group pl-0">
            <transition-group name="fade" appear>
                <li
                    class="list-group-item"
                    v-for="(item,index) in data.list"
                    @click="removeItem(index)"
                    :key="item"
                >
                    {{ item }}
                </li>
            </transition-group>
        </ul>
    </div>
    
</template>

<script setup>
    import { reactive } from 'vue';
    const data = reactive({
        list:['Francis','Ron','Martha'],
        name:''
    });

    const addOne = () => {
        if(!data.list.includes(data.name) && data.name !== ''){
            data.list.unshift(data.name)
        }
    }

    const removeItem = (index) => {
        data.list.splice(index,1)
    }
</script>

<style scoped>

    .fade-enter-from,
    .fade-leave-to {
        opacity: 0;
    }

    .fade-enter-active,
    .fade-leave-active {
        transition: 1s;
    }

    .fade-enter-to,
    .fade-leave-from {
        opacity: 1;
    }

    .fade-move {
        transition: transform 1s;
    }

</style>
