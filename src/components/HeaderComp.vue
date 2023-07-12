<template>
    <div class="header">
        <a href="/" class="logoSite">bProf</a>
        <div class="end_region">
            <div class="nav_element">
                <div class="profile">
                    <div class="box_m box_menu">
                        <i class="fa-solid fa-bars"></i>
                    </div>
                    <div class="box_m box_profile">
                        <div class="dot_profile">
                            <div class="dot_notification">
                                <span class="notification_number">3</span>
                            </div>
                            <span class="initial_letter_profile">A</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "HeaderComp"
}
</script>

<style scoped>
.header {
    position: fixed;
    z-index: 9999999;
    top: 0;
    left: 0;
    width: 100%;
    height: 85px;
    padding: 0 100px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.logoSite {
    color: #7bb985;
    font-size: 1.3rem;
    font-weight: 600;
}

.end_region,
.nav_element {
    display: flex;
    align-items: center;
}

.profile {
    display: flex;
    align-items: center;
    border: 1px solid #ddd;
    border-radius: 26px;
    padding: 6px;
    transition: box-shadow 150ms ease;
}

.profile:hover {
    box-shadow: 0 2px 5px rgba(0, 0, 0, .3);
}

.box_menu {
    width: 36px;
    height: 36px;
    aspect-ratio: 1;
    border-radius: 50%;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
}

.dot_profile {
    position: relative;
    width: 36px;
    height: 36px;
    aspect-ratio: 1;
    border-radius: 50%;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    background: #121212;
}

.dot_notification {
    position: absolute;
    top: 4px;
    right: 4px;
    transform: translate(50%, -50%);
    width: 18px;
    height: 18px;
    aspect-ratio: 1;
    border-radius: 50%;
    background: #FF3737;
    border: 1px solid #F9F9F9;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
}

.notification_number {
    color: #fff;
    font-size: 12px;
    font-weight: 600;
}

.initial_letter_profile {
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
}

/* Media Query's */
@media only screen and (max-width: 1290px) {
    .header {
        height: 50px;
        padding: 0 4%;
    }

    .box_menu,
    .dot_profile {
        width: 23px;
        height: 23px;
    }

    .initial_letter_profile,
    .box_menu i {
        font-size: .8rem;
    }

    .dot_notification {
        width: 14px;
        height: 14px;
    }

    .notification_number {
        font-size: 10px;
    }
}
</style>