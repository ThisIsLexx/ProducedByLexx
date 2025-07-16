<script setup lang="ts">
import { ref, nextTick } from 'vue'

interface Song {
    id: number;
    image: string;
    title: string;
    artist: string;
    url: string;
}

const songs: Song[] = [
    { id: 1, image: '/covers/unica.jpg', title: 'ÚNICA', artist: 'CELG', url: '/music/unica.wav' },
    { id: 2, image: '', title: 'Song Two', artist: 'Artist Two', url: 'song2.mp3' },
    { id: 3, image: '', title: 'Song Three', artist: 'Artist Three', url: 'song3.mp3' },
];

const isPlaying = ref(false);

const audioPlayer = ref<HTMLAudioElement | null>(null);
const audioSource = ref('');
const currentSong = ref<Song | null>(null);

const stopSong = () => {
    if (audioPlayer.value) {
        audioPlayer.value.pause();
        audioPlayer.value.currentTime = 0;
        audioSource.value = '';
        isPlaying.value = false;
        currentSong.value = null;
    }
};
const handleAudioEnd = () => {
    isPlaying.value = false;
    currentSong.value = null;
};
const playSong = (songId: number) => {
    isPlaying.value = false;

    const song = songs.find(s => s.id === songId);
    if (!song) return;

    if (isPlaying.value && currentSong.value === song) {
        stopSong();
        return;
    }

    currentSong.value = song || null;
    audioSource.value = song.url;
    nextTick(() => {
        if (audioPlayer.value) {
            audioPlayer.value.load();
            audioPlayer.value.play();
            isPlaying.value = true;
        } else {
            console.error('Audio player not found');
        }
    });
};


console.log('ReproductorMp3 component loaded with songs:', songs);
console.log('Audio source:', audioSource.value);

</script>

<template>
    <div class="py-8 flex flex-col items-center w-full">
        <h2 class="text-4xl font-bold mb-6 text-left w-full text-[#00FFD1]">Portafolio</h2>
        <div class="w-full flex flex-col gap-2 py-2">
            <div v-for="song in songs" :key="song.id"
                class="flex items-center justify-between p-4 bg-gray-700/30 rounded-lg shadow-md hover:shadow-lg hover:scale-101 transition-all duration-150 ease-in-out">
                <div class="w-1/3 flex items-center">
                    <img v-if="song.image" :src="song.image" alt="Cover Image" class="w-14 h-auto rounded-md">
                    <div v-else class="w-14 h-14 bg-gray-700 rounded-md justify-center flex items-center">
                        cover
                    </div>
                    <div class="flex flex-col pl-5">
                        <h3 class="text-xl font-semibold text-[#00FFD1]">{{ song.title }}</h3>
                        <p class="text-gray-400">{{ song.artist }}</p>
                    </div>
                </div>
                <div class="w-full flex items-center gap-4">
                    <button v-if="currentSong?.id === song.id && !isPlaying" @click="playSong(song.id)"
                        class="bg-[#FF5C00] text-white px-4 py-2 rounded-md hover:bg-[#FF5C00]/80 transition-all hover:cursor-pointer duration-300">
                        Play
                    </button>
                    <button v-else-if="currentSong?.id === song.id && isPlaying" @click="stopSong()"
                        class="bg-red-600 text-white px-4 py-2 rounded-md hover:bg-red-500 transition-all hover:cursor-pointer duration-300">
                        Stop
                    </button>
                    <button v-else @click="playSong(song.id)"
                        class="bg-[#FF5C00] text-white px-4 py-2 rounded-md hover:bg-[#FF5C00]/80 transition-all hover:cursor-pointer duration-300">
                        Play
                    </button>

                    <div class="flex flex-row items-center justify-center h-full w-full mx-auto">
                        <!-- ESQUELETO LOADER AUDIO -->
                        <div :class="currentSong?.id === song.id ? 'animate-pulse opacity-100' : ''"
                            class="flex gap-2 h-full items-end justify-center opacity-20">
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-2 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-6 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-2 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-2 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-2 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-4 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-8 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-5 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-3 bg-[#00FFD1] rounded-full"></div>
                            <div class="w-1 h-2 bg-[#00FFD1] rounded-full"></div>
                        </div>
                    </div>
                    <!-- BEGIN: SOCIAL MEDIA ICONS -->
                    <div class="flex gap-4 items-center w-full justify-end">
                        <a href="" class="h-8 w-8 hover:scale-110 transition-transform duration-200">
                            <img src="https://www.vectorlogo.zone/logos/spotify/spotify-icon.svg" alt="">
                        </a>
                        <a href="" class="h-8 w-8 hover:scale-110 transition-transform duration-200">
                            <img src="https://www.vectorlogo.zone/logos/soundcloud/soundcloud-icon.svg" alt="">
                        </a>
                        <a href="" class="h-8 w-8 hover:scale-110 transition-transform duration-200">
                            <img src="https://www.vectorlogo.zone/logos/apple/apple-icon.svg" alt="">
                        </a>
                        <a href="" class="h-8 w-8 hover:scale-110 transition-transform duration-200">
                            <img src="https://www.vectorlogo.zone/logos/youtube/youtube-icon.svg" alt="">
                        </a>
                        <a href="" class="h-8 w-8 hover:scale-110 transition-transform duration-200">
                            <img src="https://www.vectorlogo.zone/logos/instagram/instagram-icon.svg" alt="">
                        </a>
                    </div>
                    <!-- END: SOCIAL MEDIA ICONS -->
                </div>
            </div>
            <audio ref="audioPlayer" class="w-full" :src="audioSource" @ended="handleAudioEnd"></audio>
        </div>
    </div>

    <transition name="slide-fade">
        <div v-if="isPlaying && currentSong?.image"
            class="absolute bottom-10 left-10 w-[14rem] h-autp right-0 p-4 bg-gray-700/50 rounded-md text-white text-center">
            <div class="flex flex-col items-center h-full">
                <div class="h-3/4">
                    <img v-if="currentSong?.image" :src="currentSong?.image" alt="Cover Image"
                        class="w-full h-auto object-cover rounded-md">
                    <!-- <img v-else src="/covers/default-cover.jpg" alt="Default Cover Image"
                        class="w-full h-full object-cover rounded-md"> -->
                </div>
            </div>
            <hr class="border-t border-gray-600 w-full py-2">
            <div class="h-1/4 flex flex-col items-center">
                <p class="text-sm">{{ currentSong?.title }}</p>
                <p class="text-xs text-gray-400">{{ currentSong?.artist }}</p>
            </div>
        </div>
    </transition>

</template>