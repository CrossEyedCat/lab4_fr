<script setup>
import getFavorites from './components/getFavorites.vue';
import getFolders from './components/getFolders.vue';
import getFolderSongs from './components/getFolderSongs.vue';
import getHistory from './components/getHistory.vue';
import getLevels from './components/getLevels.vue';
import getMarks from './components/getMarks.vue';
import getSingers from './components/getSingers.vue';
import getSongs from './components/getSongs.vue';
import getSongSingers from './components/getSongSingers.vue';
import getTags from './components/getTags.vue';
import getTagSongs from './components/getTagSongs.vue';

import saveComment from './components/saveComment.vue';
import saveFavorite from './components/saveFavorite.vue';
import saveFolder from './components/saveFolder.vue';
import saveFolderSong from './components/saveFolderSong.vue';
import saveHistory from './components/saveHistory.vue';
import saveLevel from './components/saveLevel.vue';
import saveMark from './components/saveMark.vue';
import saveSinger from './components/saveSinger.vue';
import saveSong from './components/saveSong.vue';
import saveSongSinger from './components/saveSongSinger.vue';
import saveTag from './components/saveTag.vue';
import saveTagSong from './components/saveTagSong.vue';
</script>

<template>
  <div>
    <getFavorites></getFavorites>
    <getFolders></getFolders>
    <getFolderSongs></getFolderSongs>
    <getHistory></getHistory>
    <getLevels></getLevels>
    <getMarks></getMarks>
    <getSingers></getSingers>
    <getSongs></getSongs>
    <getSongSingers></getSongSingers>
    <getTags></getTags>
    <getTagSongs></getTagSongs>

    <saveComment></saveComment>
    <saveFavorite></saveFavorite>
    <saveFolder></saveFolder>
    <saveFolderSong></saveFolderSong>
    <saveHistory></saveHistory>
    <saveLevel></saveLevel>
    <saveMark></saveMark>
    <saveSinger></saveSinger>
    <saveSong></saveSong>
    <saveSongSinger></saveSongSinger>
    <saveTag></saveTag>
    <saveTagSong></saveTagSong>
  </div>
</template>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>