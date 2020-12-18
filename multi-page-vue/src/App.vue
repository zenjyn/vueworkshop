<template>
    <h1>Multi Page Vue</h1>
    <nav>
        <ul>
            <li
                v-for="navigationLink in navigationLinks"
                :key="navigationLink.slug"
                :class="{ active: currentPage === navigationLink.slug }"
            >
                <a @click.prevent="setCurrentPage(navigationLink.slug)" href="#">{{ navigationLink.label }}</a>
            </li>
        </ul>
    </nav>
    <component :is="currentPage" :data="currentProps" />
</template>

<script>
import PageOne from '@/components/PageOne.vue';
import PageTwo from '@/components/PageTwo.vue';
import PageThree from '@/components/PageThree.vue';

export default {
    name: 'App',
    components: {
        PageOne,
        PageTwo,
        PageThree,
    },
    data() {
        return {
            currentPage: "PageOne",
            currentProps: {},
        };
    },
    computed: {
        navigationLinks() {
            return [{
                slug: "PageOne",
                label: "Page One",
            },{
                slug: "PageTwo",
                label: "Page Two",
            },{
                slug: "PageThree",
                label: "Page Three",
            }];
        },
        pageProps() {
            return {
                pageOne: {},
                pageTwo: {
                    message: "Oi!",
                },
                pageThree: {},
            }
        }
    },
    methods: {
        setCurrentPage(newPage) {
            this.currentPage = newPage;
            this.currentProps = this.pageProps[newPage];
        },
    },
};
</script>

<style>
nav li a {
    color: inherit;
}
nav ul {
    list-style: none;
    padding: 0;
}
nav li {
    display: inline-block;
    text-decoration: none;
}
nav li.active {
    color: purple;
}
nav li + li {
    margin-left: 24px;
}
</style>
