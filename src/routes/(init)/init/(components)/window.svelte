<script lang="ts">
    import { classNames } from '$lib/utils/classnames';
    import type { Snippet } from 'svelte';

    interface Props {
        class?: string;
        link?: Snippet;
        title?: Snippet;
        children: Snippet;
    }

    let { class: className = '', link, title, children }: Props = $props();
</script>

<div
    class={classNames(
        'bg-smooth relative z-10 container mx-auto flex flex-col rounded-2xl p-1 backdrop-blur-2xl',
        'before:absolute before:inset-x-0 before:top-0 before:h-px before:bg-linear-to-r before:from-transparent before:via-white/30 before:to-transparent',
        className
    )}
>
    <div class="relative flex items-center justify-between px-1.5 pt-1 pb-2">
        {#if link}
            <span
                class="font-aeonik-fono tracking-loose text-micro text-primary absolute flex pl-2 uppercase"
                >{@render link()}</span
            >
        {:else}
            <svg
                width="20"
                height="20"
                viewBox="0 0 20 20"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
            >
                <path
                    fill-rule="evenodd"
                    clip-rule="evenodd"
                    d="M8.85993 15.9082C9.1532 16.1887 9.42886 16.3008 9.67815 16.3008C9.92743 16.3008 10.2031 16.1887 10.4964 15.9082C10.7921 15.6254 11.0813 15.1923 11.335 14.6187C11.7947 13.5793 12.1058 12.1513 12.1596 10.5412L7.19664 10.5412C7.25046 12.1513 7.56154 13.5793 8.02129 14.6187C8.27499 15.1923 8.56414 15.6254 8.85993 15.9082ZM6.19613 10.5412C6.25014 12.2655 6.5818 13.8363 7.10675 15.0232C7.24724 15.3408 7.40393 15.6363 7.57643 15.9022C5.46084 15.0694 3.90506 13.0155 3.71892 10.5412L6.19613 10.5412ZM3.71892 9.54119L6.19613 9.54118C6.25014 7.81689 6.5818 6.24603 7.10675 5.05917C7.24724 4.74154 7.40393 4.44609 7.57643 4.18017C5.46084 5.01297 3.90505 7.06689 3.71892 9.54119ZM7.19664 9.54118L12.1596 9.54118C12.1058 7.93106 11.7948 6.5031 11.335 5.46367C11.0813 4.89009 10.7921 4.45701 10.4964 4.17415C10.2031 3.89371 9.92743 3.78158 9.67815 3.78158C9.42886 3.78158 9.1532 3.89371 8.85993 4.17415C8.56414 4.45701 8.27499 4.89009 8.02129 5.46367C7.56154 6.5031 7.25046 7.93106 7.19664 9.54118ZM13.1602 9.54118C13.1061 7.81689 12.7745 6.24603 12.2495 5.05917C12.109 4.74154 11.9524 4.44609 11.7799 4.18017C13.8955 5.01297 15.4512 7.06689 15.6374 9.54118L13.1602 9.54118ZM15.6374 10.5412C15.4512 13.0155 13.8955 15.0694 11.7799 15.9022C11.9524 15.6363 12.109 15.3408 12.2495 15.0232C12.7745 13.8363 13.1061 12.2655 13.1602 10.5412L15.6374 10.5412ZM16.6561 10.0412C16.6561 6.05208 13.5518 2.78158 9.67815 2.78158C5.80449 2.78158 2.7002 6.05208 2.7002 10.0412C2.7002 14.0303 5.80449 17.3008 9.67815 17.3008C13.5518 17.3008 16.6561 14.0303 16.6561 10.0412Z"
                    fill="#E4E4E7"
                />
            </svg>
        {/if}

        {#if title}
            <span
                class="font-aeonik-fono tracking-loose text-micro text-primary mx-auto block text-center uppercase"
                >{@render title()}</span
            >
        {/if}
    </div>

    {@render children()}
</div>
