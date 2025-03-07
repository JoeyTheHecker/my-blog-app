<template>
    <div>
        <ul>
            <li>
                <NuxtLink to="">Home</NuxtLink>
            </li>
            <li>
                <NuxtLink to="">Articles</NuxtLink>
            </li>
            <li>
                <NuxtLink to="">Register</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/blog/about">About</NuxtLink>
            </li>
        </ul>
    </div>

    <div>
        <slot></slot>
    </div>

    <div>
        <h1> this is the foorter</h1>
    </div>
</template>