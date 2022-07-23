<template>
    <div class="overflow-hidden bg-white sm:px-6 lg:px-10">
    <label for="email" class="block text-sm font-medium text-gray-700">Add item</label>
    <div class="flex mt-1 rounded-md shadow-sm">
        <div class="relative flex items-stretch flex-grow focus-within:z-10">
        <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
            <!-- Heroicon name: solid/users -->
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01" />
            </svg>
        </div>
        <input v-model="item.name" type="text" id="name" class="block w-full pl-10 border-gray-300 rounded-none focus:ring-indigo-500 focus:border-indigo-500 rounded-l-md sm:text-sm" placeholder="Input Task">
        </div>
        <button :class="[item.name ? 'active' : 'notactive']" @click="addItem()" type="button" class="relative inline-flex items-center px-4 py-2 -ml-px space-x-2 text-sm font-medium text-gray-700 border border-gray-300 rounded-r-md bg-gray-50 hover:bg-gray-100 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500">
        <!-- Heroicon name: solid/sort-ascending -->
        <span>Add</span>
        </button>
    </div>
    </div>
    <!-- <div class="mt-3">
        <h2>add item form</h2>
        <div class="container m-2 w-100">
            <input
                type="test"
                placeholder="add item"
                class="border"
                v-model="item.name"
            />
            <button
                :class="[item.name ? 'active' : 'notactive']"
                @click="addItem()"
            >
                add +
            </button>
        </div>
    </div> -->
</template>
<script>
export default {
    data: function() {
        return {
            item: {
                name: ""
            }
        };
    },
    methods: {
        addItem() {
            if (this.item.name == "") {
                return;
            }
            axios
                .post("api/item/store", {
                    item: this.item
                })
                .then(res => {
                    if (res.status == 201) {
                        this.item.name = "";
                        this.$emit("reloadlist");
                    }
                })
                .catch(error => {
                    console.log(error);
                });
        }
    }
};
</script>

<style scoped>
.active {
    color: white;
    background-color: blue;
}
.inactive {
    color: gray;
}
</style>
