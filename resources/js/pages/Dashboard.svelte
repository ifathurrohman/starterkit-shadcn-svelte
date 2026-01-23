<script lang="ts">
    import AppLayout from "@/layouts/AppLayout.svelte";
    import { type BreadcrumbItem } from "@/types";

    const breadcrumbs: BreadcrumbItem[] = [
        {
            title: "Dashboard",
            href: "/dashboard"
        },
    ];
</script>

<svelte:head>
    <title>Dashboard</title>
</svelte:head>

<AppLayout {breadcrumbs}>
    <h1 class="text-3xl font-bold">Dashboard</h1>
    <p>Welcome to your dashboard!</p>
</AppLayout>
