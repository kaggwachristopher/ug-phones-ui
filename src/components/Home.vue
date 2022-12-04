<template>
    <v-app class="home-app-wrapper">
        <v-container :class="'home-container'">
            <v-row no-gutters>
                <v-col cols="12" sm="6" class="d-flex align-end justify-center pa-2">
                    <v-text-field focused v-model="phoneNumber" filled label="Enter number" class="number-input"
                        required></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" class="d-flex align-end justify-center pa-2">
                    <transition name="slide-fade" mode="out-in">
                        <span :key="provider" class="provider-text">{{ provider }}</span>
                    </transition>
                </v-col>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
import { defineComponent } from 'vue'
import ugPhone from "ug-phone";

export default defineComponent({
    name: 'Home',
    data() {
        return {
            phoneNumber: ""
        }
    },

    computed: {
        provider() {
            return ugPhone.getUgandanProvider(this.phoneNumber) || "No provider";
        }
    }
});
</script>

<style>
.home-app-wrapper .v-application__wrap {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-image: url(../assets/background.jpg);
    background-size: cover;
}

.home-container {
    width: 50vw !important;
    border-radius: 8px 0px 8px 0px;
    background-color: #ffd04ad4;
    color: #953553;
}

.home-container .v-col-sm-6 {
    padding: 8px;
}

.provider-text {
    font-size: x-large;
    font-weight: 650;
    font-family: Calibri, 'Gill Sans', 'Gill Sans MT', 'Trebuchet MS', sans-serif
}

.number-input .v-input__details {
    display: none;
}

.slide-fade-enter-active {
    transition: all .3s ease;
}

.slide-fade-leave-active {
    transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}

.slide-fade-enter,
.slide-fade-leave-to {
    transform: translateX(10px);
    opacity: 0;
}
</style>