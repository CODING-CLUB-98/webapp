<template>
    <div class="sidepage" v-if="classs">
        <div class="profile">
            <profile-image class="w-28" :src="classs.subject.image" alt="class picture"/>
            <h3>{{ classs.subject.sub_code }} - {{ classs.subject.sub_name }}</h3>
            <p> {{ classs.batch.stream }} - S{{ classs.semester.sem }} </p>
        </div>
        <div class="navigation">
            <aside>
                <ul>
                <li>
                    <router-link to="/">
                        <span class="material-symbols-outlined">home</span>

                        <span class="mx-4"> Home </span>
                    </router-link>
                </li>

                <li v-if="classs.is_lab">
                    <router-link to="/labs">
                        <span class="material-symbols-outlined">desktop_windows</span>

                        <span class="mx-4"> Lab </span>
                    </router-link>
                </li>

                <li v-if="classs.is_lab">
                    <router-link to="/exam">
                        <span class="material-symbols-outlined">notes</span>

                        <span class="mx-4"> Exam </span>
                    </router-link>
                </li>

                <li>
                    <router-link to="/resources">
                        <span class="material-symbols-outlined">book</span>

                        <span class="mx-4"> Resources </span>
                    </router-link>
                </li>

                <li>
                    <router-link to="/analysis">
                        <span class="material-symbols-outlined">school</span>

                        <span class="mx-4"> Student Analysis </span>
                    </router-link>
                </li>

                <li v-if="classs.owner.id == user.id">
                    <router-link to="/settings">
                        <span class="material-symbols-outlined">settings</span>

                        <span class="mx-4"> Settings </span>
                    </router-link>
                </li>

                <li>
                    <a href="/logout">
                        <span class="material-symbols-outlined">logout</span>

                        <span class="mx-4"> Logout </span>
                    </a>
                </li>

                </ul>

            </aside>
            
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import ProfileImage from '@/components/ProfileImage.vue'
import { mapGetters } from 'vuex'

export default({
    name: 'Navigation',
    components: {
        ProfileImage,
    },
    data(){
        return {
        }
    },
    computed: {
        ...mapGetters([
            'classs',
        ]),
        ...mapGetters('auth', [
            'user',
        ]),
    }
})
</script>
