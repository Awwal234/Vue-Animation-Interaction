<script setup lang="ts">
import { ref, onMounted } from 'vue'
const suggestions = ["Tasks", "Actions", "People", "Teams"]
const members = [
  {
    image: '/img/personone.svg',
    name: 'Stephen Baskman',
    email: 'baskmandem@syvest.com'
  },
  {
    image: '/img/persontwo.svg',
    name: 'Rodrigrouz Declan-Rice',
    email: 'declanriceaflred@syvest.com'
  },
]
const history_amount = ref(members.length)
const tasks = ref('4')
const actions = ref('8')

const sug_anime = () => {
  //@ts-ignore
  let mm = gsap.matchMedia();
  //@ts-ignore
  gsap.fromTo('#suggestions', { x: -170, opacity: 0.5 }, { x: 0, opacity: 1, duration: 4 })
  //@ts-ignore
  gsap.fromTo('#members', { y: 50, x: 4, duration: 4, position: 'relative', opacity: 0.3 }, { y: 0, opacity: 1, x: 0, duration: 8 })
  mm.add("(min-width: 768px)", () => {

    // this setup code only runs when viewport is at least 800px wide
    //@ts-ignore
    gsap.fromTo('#first', { y: -50, width: '0px', duration: 4, position: 'relative', opacity: 0.1 }, { y: 0, opacity: 1, width: '100%', duration: 2 });
    //@ts-ignore
    gsap.fromTo('#second', { y: 50, width: '0px', duration: 4, position: 'relative', opacity: 0.1 }, { y: 0, opacity: 1, width: '100%', duration: 2 });
    //@ts-ignore
    gsap.fromTo('#third', { y: 0, transformOrigin: "100% 50%", ease: Power0.easeNone, x: 40, width: '0px', duration: 4, position: 'relative', opacity: 0.1 }, { y: 0, x: 0, opacity: 1, width: '40%', duration: 2 });
  })
  mm.add("(max-width: 767px)", () => {

    // this setup code only runs when viewport is at least 800px wide
    //@ts-ignore
    gsap.fromTo('#first', { y: -50, width: '0px', duration: 4, position: 'relative', opacity: 0.3 }, { y: 0, opacity: 1, width: '100%', duration: 2 });
    //@ts-ignore
    gsap.fromTo('#second', { y: 50, width: '0px', duration: 4, position: 'relative', opacity: 0.1 }, { y: 0, opacity: 1, width: '100%', duration: 2 });
    //@ts-ignore
    gsap.fromTo('#third', { y: -50, width: '0px', duration: 4, position: 'relative', opacity: 0.3 }, { y: 0, opacity: 1, width: '100%', duration: 2 });
  })
}

onMounted(() => {
  sug_anime()
})
</script>

<template>
  <main class="bg-[#F8F9FB] md:bg-[#fff] md:pb-[30px]">
    <div class="md:bg-[#F8F9FB] md:w-[430px] md:mt-[30px] md:mx-auto">
      <!--header section-->
      <div class="flex pb-[19px] justify-between items-center px-[16px] py-[17px]">
        <div class="flex items-center">
          <div class="w-fit h-fit pr-[17px] border-r border-[#EAEDF6]">
            <img src="/img/newsearch.svg" class="" alt="" loading="lazy" />
          </div>
          <div>
            <input type="text" placeholder="start a search"
              class="pl-[16px] text-[14px] text-[#8B8698] leading-[17.64px] bg-[transparent] border-none w-[200px] md:w-[277px] focus:outline-none" />
          </div>
        </div>
        <!--one end flex-->
        <div class="flex space-x-[5.67px] items-center">
          <div><img src="/img/Command.svg" class="" alt="" loading="lazy" /></div>
          <div><img src="/img/Vector.svg" class="" alt="" loading="lazy" /></div>
        </div>
        <!--end all-->
      </div>
      <!--end header sect-->
      <div class="border-b border-[#EAEDF6]"></div>
      <div class="px-[16px] pb-[17px] mt-[16px]">
        <div class="text-[12px] font-[400] text-[#8B8698] leading-[15.12px]">What are you looking for?</div>
        <div class="mt-[16px] s_scroll flex overflow-x-scroll space-x-[16px] items-center">
          <div id="suggestions"
            class="w-[80px] font-[400] text-[12px] leading-[15.12px] text-[#242938] list text-center h-fit bg-[transparent] p-[8px] rounded-[40px]"
            v-for="items in suggestions" :key="items">
            <div class="flex justify-center items-center space-x-[4px]">
              <div><img src="/img/cancel.svg" alt="" loading="lazy" /></div>
              <div>{{ items }}</div>
            </div>
          </div>
        </div>
        <!--suggestions end-->
        <!--history begin-->
        <div id="history_s" class="mt-[24px] overflow-y-scroll">
          <div class="flex items-center justify-between">
            <div class="flex items-center space-x-[4px]">
              <div class="font-[400] text-[#8B8698] text-[12px] leading-[15.12px]">History</div>
              <div
                class="bg-[#E2E7F3] font-[600] text-[8px] text-[#242938] leading-[10.08px] w-fit rounded-[8px] py-[2px] px-[5px]">
                {{ history_amount }}
              </div>
            </div>
            <div class="font-[400] text-[#A09CAB] text-[10px] leading-[12.6px]">View All</div>
          </div>
          <!--end flex in history-->
          <div id="members" class="mt-[24px] space-y-[16px]" v-for="member in members" :key="member.name">
            <div class="flex flex-nowrap items-center">
              <div class="w-[32px]"><img :src="member.image" class="" loading="lazy" /></div>
              <div class="pl-[8px] w-[140px] leading-[15.12px] font-[600] text-[12px] text-[#242938]">
                {{ member.name }}
              </div>
              <div class="ml-[8px] w-fit email py-[2px] px-[8px] leading-[15.12px] font-[400] text-[10px] text-[#8B8698]">
                {{ member.email }}
              </div>
            </div>
          </div>
          <!---->
        </div>
        <!--end history-->
        <div class="mt-[24px] border border-[#EAEDF6]"></div>
        <div class="flex mt-[24px] items-center space-x-[4px]">
          <div class="font-[400] text-[#8B8698] text-[12px] leading-[15.12px]">Tasks</div>
          <div
            class="bg-[#E2E7F3] font-[600] text-[8px] text-[#242938] leading-[10.08px] w-fit rounded-[8px] py-[2px] px-[5px]">
            {{ tasks }}
          </div>
        </div>
        <!--task-->
        <div id="task_s" class="mt-[24px] md:space-x-[8px] md:flex">
          <div class="md:w-[60%]">
            <div id="first" class="w-full flex space-x-[8px] rounded-[8px] bg-[#E9EDF6] p-[16px]">
              <div class="w-[20%]">
                <div class="w-[32px] h-[32px] bg-[#fff] p-[8px] rounded-[500px] border border-[#CCD6EA]"></div>
              </div>
              <div class="w-[80%]">
                <div class="flex justify-between items-center">
                  <div class="font-[600] text-[#242938] text-[12px] leading-[15.12px]">Design For Apple</div>
                  <div class="w-fit"><input type="checkbox" class="w-[16px] h-[16px]" /></div>
                </div>
                <div class="mt-[9px] tight-[-4%] font-[500] text-[#767184] text-[10px] leading-[15px]">
                  Sketch an apple self-driving car powered by nature that stimulates a metaverse.
                </div>
              </div>
              <!---->
            </div>
            <!--end one-->
            <!--begin two-->
            <div id="second" class="w-full mt-[8px] flex space-x-[8px] rounded-[8px] bg-[#FCE5E3] p-[16px]">
              <div class="w-[20%]">
                <div class="w-[32px] h-[32px] bg-[#fff] p-[8px] rounded-[500px] border border-[#FBDDDA]"></div>
              </div>
              <div class="w-[80%]">
                <div class="flex justify-between items-center">
                  <div class="font-[600] text-[#EB4335] text-[12px] leading-[15.12px]">Manage For Tesla</div>
                  <div class="w-fit"><input type="checkbox" class="w-[16px] h-[16px]" /></div>
                </div>
                <div class="mt-[9px] tight-[-4%] font-[500] text-[#767184] text-[10px] leading-[15px]">
                  Space-rocket III will be launched soon, manage the safety & guide department.
                </div>
              </div>
              <!---->
            </div>
            <!--end two-->
            <!---->
          </div>
          <!--second row flex or block-->
          <div id="third" class="w-full mt-[8px] md:mt-[0px] md:w-[40%] rounded-[8px] bg-[#DDE9FD] p-[16px]">
            <div class="md:w-[100%] w-full">
              <div class="flex justify-between items-center">
                <div class="w-[32px] h-[32px] bg-[#fff] p-[8px] rounded-[500px] border border-[#B7D0FB]"></div>
                <div class="w-fit"><input type="checkbox" class="w-[16px] h-[16px]" /></div>
              </div>
              <div class="font-[600] mt-[8px] text-[#4285F4] text-[12px] leading-[15.12px]">Market For Google</div>
              <div class="mt-[8px] tight-[-4%] font-[500] text-[#767184] text-[10px] leading-[15px]">
                The Google X Microsoft AI powered search ‘Binge’ is to go live soon, drive an inclusive community for
                Binge.
              </div>
            </div>
            <!---->
          </div>
          <!--end second-->
        </div>
        <!--end task-->
        <div class="mt-[22px] border border-[#EAEDF6]"></div>
        <div class="flex items-center mt-[24px] justify-between">
          <div class="flex items-center space-x-[4px]">
            <div class="font-[400] text-[#8B8698] text-[12px] leading-[15.12px]">Actions</div>
            <div
              class="bg-[#E2E7F3] font-[600] text-[8px] text-[#242938] leading-[10.08px] w-fit rounded-[8px] py-[2px] px-[5px]">
              {{ actions }}
            </div>
          </div>
          <div class="font-[400] text-[#A09CAB] text-[10px] leading-[12.6px]">View All</div>
        </div>
        <!--actions-->
        <!--end actions-->
      </div>
      <!---->
    </div>
  </main>
</template>

<style scoped>
main {
  min-height: 100vh;
}

.list {
  border: 1px solid #EAEDF6;
  filter: drop-shadow(0px 1px 4px rgba(0, 0, 0, 0.08));
}

.s_scroll::-webkit-scrollbar {
  display: none;
}

#history_s::-webkit-scrollbar {
  display: none;
}

#task_s::-webkit-scrollbar {
  display: none;
}

.email {
  background: linear-gradient(90deg, #EDF0F8 19.2%, rgba(241, 243, 249, 0.05) 100%);
}
</style>
