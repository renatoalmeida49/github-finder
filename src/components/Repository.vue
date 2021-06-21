<template>
<v-card
    width="315"
>
    <v-card-title>
        {{ repository.name }}
    </v-card-title>

    <v-card-subtitle>
        {{ repository.description }}
    </v-card-subtitle>

    <v-card-actions>
        {{ repository.language }}
        {{ repository.stargazers_count }}
        {{ repository.forks }}
    </v-card-actions>
</v-card>
</template>

<script>
export default {
    name: "Repository",
    props: {
        repository: {
            required: true
        }
    }
}
</script>

<style>

</style>