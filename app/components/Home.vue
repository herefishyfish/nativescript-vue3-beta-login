<script lang="ts" setup>
import {
  ref,
  computed,
  onMounted,
  onUnmounted,
  $navigateTo,
} from 'nativescript-vue';
import Details from './Details.vue';

const counter = ref(0);
const message = computed(() => {
  return `Blank {N}-Vue app: ${counter.value}`;
});

function logMessage() {
  console.log('You have tapped the message!');
}

let interval: any;
onMounted(() => {
  console.log('mounted');
  interval = setInterval(() => counter.value++, 100);
});

onUnmounted(() => {
  console.log('unmounted');
  clearInterval(interval);
});
</script>

<template>
  <Frame>
    <Page actionBarHidden="true">
      <ScrollView>
        <StackLayout>
          <!-- 
        `*` to fill the space above the labels
        `auto` for text fields
        `100` for Device Independant pixels to padd the bottom of the image
        -->
          <GridLayout rows="* auto auto 100">
            <Image
              class="w-full"
              stretch="aspectFill"
              rowSpan="4"
              src="~/assets/Path_1.png"
            />

            <Label
              row="1"
              verticalAlignment="bottom"
              text="Velkommen Tilbage!"
              class="text-3xl text-white px-12"
            ></Label>
            <Label
              row="2"
              verticalAlignment="top"
              text="pil ved mig moussa"
              class="text-lg text-white px-12"
            ></Label>
          </GridLayout>

          <Label
            class="font-bold text-lg mx-4 mb-2 text-gray-300"
            text="Email"
          ></Label>
          <TextField
            class="py-4 text-black px-4 mx-4 bg-gray-100 border-none rounded-md"
            hint="Enter text..."
          />

          <!-- Everything else inside the scroll view -->
          <Button
            @tap="$navigateTo(Details)"
            class="
              my-4
              px-4
              py-2
              dark:text-black
              bg-white
              border-2 border-blue-400
              rounded-lg
            "
            horizontalAlignment="center"
          >
            View Details
          </Button>
          <GridLayout columns="* auto *">
            <StackLayout class="bg-gray-300 h-1 mx-4"></StackLayout>
            <StackLayout class="bg-gray-300 h-1 mx-4" col="2"></StackLayout>

            <Label col="1" text="Eller" class="mx-4"></Label>
          </GridLayout>
          <Button
            @tap="$navigateTo(Details)"
            class="
              my-4
              px-4
              py-2
              dark:text-black
              bg-white
              border-2 border-blue-400
              rounded-lg
            "
            horizontalAlignment="center"
          >
            View Details
          </Button>
        </StackLayout>
      </ScrollView>
    </Page>
  </Frame>
</template>

<style>
/* .info {
    font-size: 20;
  } */
</style>
