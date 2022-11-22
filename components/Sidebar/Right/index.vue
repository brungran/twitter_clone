<template>
    <div class="flex flex-col">
        
        <!-- Preview Card: What's Happening -->
        <SidebarRightPreviewCard title="What's Happening">
            
            <SidebarRightPreviewCardItem v-for="whatsHappeningItem in whatsHappeningItems">
                <h2 class="font-bold text-gray-800 text-md dark:text-white">{{whatsHappeningItem.title}}</h2>
                <p class="text-xs text-gray-400">{{whatsHappeningItem.count}}</p>
            </SidebarRightPreviewCardItem>

        </SidebarRightPreviewCard>
        
        <!-- Preview Card: Who to Follow -->
        <SidebarRightPreviewCard title="Who to Follow">
            <SidebarRightPreviewCardItem v-for="whoTofollowItem in whoToFollowItems">
                <div class="flex flex-row items-center justify-between p-2">
                    <div class="flex flex-row">
                        <img :src="whoTofollowItem.picture.thumbnail" :alt="whoTofollowItem.login.username" class="w-10 h-10 rounded-full">

                        <div class="flex flex-col ml-2">
                            <h1 class="text-sm font-bold text-gray-900 dark:text-white">{{whoTofollowItem.name.first}} {{whoTofollowItem.name.last}}</h1>
                            <p class="text-sm text-gray-400">@{{whoTofollowItem.login.username}}</p>
                        </div>
                    </div>

                    <div class="flex h-full">
                        <button class="px-4 py-2 font-bold text-xs text-white dark:text-black bg-black dark:bg-white rounded-full">Follow</button>
                    </div>
                </div>
            </SidebarRightPreviewCardItem>
        </SidebarRightPreviewCard>
        
    </div>
</template>

<script setup>

    const randomUser = async () => {
        const res = await fetch('https://randomuser.me/api/')
        const data = await res.json()
        return data.results[0]
    }

    const whatsHappeningItems = ref([
        {
            title: 'SpaceX',
            count: '18.8k Tweets'
        },
        {
            title: '#CodingIsFun',
            count: '8.8k Tweets'
        },
        {
            title: 'artforall',
            count: '1.8k Tweets'
        }
    ])

    const whoToFollowItems = ref([])

    whoToFollowItems.value.push(await randomUser())
    whoToFollowItems.value.push(await randomUser())
    whoToFollowItems.value.push(await randomUser())

</script>