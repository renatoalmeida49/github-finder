<template>
<div>
    {{ repository.name }}
    {{ repository.description }}

    {{ repository.language }}
    {{ repository.stargazers_count }}
    {{ repository.forks }}
</div>
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