<template>
    <div class="champ-select" v-if="state && state.localPlayer" :style="background">
        <summoner-picker :state="state" :show="pickingSummonerSpell" :first="pickingFirstSummonerSpell" @close="pickingSummonerSpell = false"></summoner-picker>
        <champion-picker :state="state" :show="pickingChampion" @close="pickingChampion = false"></champion-picker>
        <skin-picker :state="state" :show="pickingSkin" @close="pickingSkin = false"></skin-picker>

        <timer :state="state"></timer>
        <members :state="state"></members>
        <player-settings :state="state" @spell="(pickingSummonerSpell = true, pickingFirstSummonerSpell = $event)" @expand="pickingChampion = true" @skins="pickingSkin = true" @runes="showingRuneOverlay = true"></player-settings>
        <rune-editor :show="showingRuneOverlay" @close="showingRuneOverlay = false"></rune-editor>
    </div>
</template>

<script lang="ts" src="./champ-select.ts"></script>

<style lang="stylus" scoped>
    @import "../../common.styl"

    .champ-select
        z-index 10000
        position absolute
        top 0
        left 0
        bottom 0
        right 0
        background-size cover
        background-repeat no-repeat
</style>