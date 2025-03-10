<template>
    <div>
        <ul>
            <li>
                <NuxtLink to="/">Home</NuxtLink>
            </li>
            <li>
                <NuxtLink to="">Articles</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/blog/about">About</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/blog/contact">Contact</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/auth/login">Login</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/auth/register">Register</NuxtLink>
            </li>
        </ul>
    </div>

    <div>
        <NuxtPage></NuxtPage>
    </div>

    <div>
        <h1> this is the foorter</h1>
    </div>
</template>