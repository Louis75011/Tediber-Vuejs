<template>
    <div class="expand-container">
        <div class="header">
            {{title}}
            <img :src="open ? '/assets/menu-footer.png' : '/assets/menu-main.png'" @click="open = !open" alt="arrow" />
        </div>
        <div class="content" v-if="open">
            <slot />
        </div>
    </div>
</template>

<script>
    export default {
        name: "ExpandBox",
        props: {
            title: {
                type: String,
                required: true,
                default: "",
            },
            isOpen: {
                type: Boolean
            },
        },
        data(props) {
            return {
                open: props.isOpen,
            }
        }
    }
</script>

<style scoped lang="scss">
    .expand-container {
        border-top: 1px solid black;
        border-bottom: 1px solid black;

        +.expand-container {
            border-top: none;
        }

        .header {
            padding: 0.5rem 0 0.75rem 0.25rem;
            display: flex;
            justify-content: space-between;

            img {
                height: 1.5rem;
                cursor: pointer;
            }
        }

        .content {
            padding: 1rem 0.5rem;
        }
    }

    @media (max-width : 640px) {
        footer .expand-container {
            .header {
                padding-left: 2rem;
                padding-right: 0.75rem;
            }
        }
    }
</style>