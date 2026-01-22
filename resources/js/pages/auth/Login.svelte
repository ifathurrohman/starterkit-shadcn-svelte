<script lang="ts">
    import InputError from '@/components/InputError.svelte';
    import { Input } from '@/components/ui/input';
    import { Label } from '@/components/ui/label';
    import { Checkbox } from '@/components/ui/checkbox';
    import AuthBase from '@/layouts/AuthLayout.svelte';
    import type { BaseFormSnippetProps } from '@/types/forms';
    import { Form } from '@inertiajs/svelte';
    import { Button } from '@/components/ui/button';
    import { Spinner } from '@/components/ui/spinner';

    interface Props {
        status?: string;
    }

    let { status }: Props = $props();
</script>

<svelte:head>
    <title>Login</title>
</svelte:head>

<AuthBase title="Login" description="Silahkan login">
    {#if status}
        <div class="mb-4 text-center text-sm font-medium text-green-600">
            {status}
        </div>
    {/if}

    <Form method="post" action={route('login')} class="flex flex-col gap-6">
        {#snippet children({ errors, processing }: BaseFormSnippetProps)}
            <div class="grid gap-6">
                <div class="grid gap-2">
                    <Label for="email">Email</Label>
                    <Input
                        id="email"
                        name="email"
                        type="email"
                        required
                        autofocus
                        tabindex={1}
                        autocomplete="email"
                        placeholder="email@provider.com"
                    />
                    <InputError message={errors.email} />
                </div>
                <div class="grid gap-2">
                    <Label for="email">Password</Label>
                    <Input
                        id="password"
                        name="password"
                        type="password"
                        required
                        autofocus
                        tabindex={2}
                        autocomplete="current-password"
                        placeholder="Password"
                    />
                    <InputError message={errors.password} />
                </div>
                <div class="flex items-center justify-between">
                    <Label for="remember" class="flex items-center space-x-3">
                        <Checkbox id="remember" name="remember" tabindex={3} />
                        <span>Remember me</span>
                    </Label>
                </div>
                <Button type="submit" class="mt-4 w-full" tabindex={4} disabled={processing}>
                    {#if processing}
                        <Spinner />
                    {/if}
                    Log in
                </Button>
            </div>
        {/snippet}
    </Form>
</AuthBase>
