<template>
    <div class="popup">
        <div class="popup-inner">
            <slot />
            <button class="popup-close">Close Popup</button>
        </div>
    </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.popup {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 100;
    background-color: rgba(0, 0, 0, 0.2);

    display: flex;
    align-items: center;
    justify-content: center;

    .popup-inner {
        background-color: #fff;
        padding: 20px;
        border-radius: 5px;
        max-width: 500px;
        max-height: 500px;
        overflow: auto;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}
</style>