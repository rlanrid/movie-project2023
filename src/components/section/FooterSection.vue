<template>
    <footer id="footer">
        <div class="footer__inner">
            <div class="text">Copyright ⓒ 2023 rladnrider. All rights reserved.</div>
        </div>
    </footer>
</template>

<style lang="scss">
#footer {
    width: 100%;
    height: 300px;
    background-color: var(--black);

    .footer__inner {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

        .text {
            text-align: center;
        }
    }
}
</style>