<template>
  <section
    class="relative isolate overflow-hidden bg-white px-6 py-24 sm:py-32 lg:px-8"
  >
    <div
      v-if="alert"
      id="toast-default"
      class="flex items-center w-full max-w-xs p-4 text-gray-500 bg-white rounded-lg shadow dark:text-gray-400 dark:bg-gray-800"
      role="alert"
    >
      <div
        class="inline-flex items-center justify-center flex-shrink-0 w-8 h-8 text-blue-500 bg-blue-100 rounded-lg dark:bg-blue-800 dark:text-blue-200"
      >
        <svg
          class="w-4 h-4"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="red"
          viewBox="0 0 18 20"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M15.147 15.085a7.159 7.159 0 0 1-6.189 3.307A6.713 6.713 0 0 1 3.1 15.444c-2.679-4.513.287-8.737.888-9.548A4.373 4.373 0 0 0 5 1.608c1.287.953 6.445 3.218 5.537 10.5 1.5-1.122 2.706-3.01 2.853-6.14 1.433 1.049 3.993 5.395 1.757 9.117Z"
          />
        </svg>
        <span class="sr-only">Fire icon</span>
      </div>
      <div class="ms-3 text-sm font-normal">
        Gif Description Can Not Be Null.
      </div>
    </div>

    <div
      v-if="anscount"
      id="toast-success"
      class="flex items-center w-full max-w-xs p-4 mb-4 text-gray-500 bg-white rounded-lg shadow dark:text-gray-400 dark:bg-gray-800"
      role="alert"
    >
      <div
        class="inline-flex items-center justify-center flex-shrink-0 w-8 h-8 text-green-500 bg-green-100 rounded-lg dark:bg-green-800 dark:text-green-200"
      >
        <svg
          class="w-5 h-5"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="currentColor"
          viewBox="0 0 20 20"
        >
          <path
            d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5Zm3.707 8.207-4 4a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L9 10.586l3.293-3.293a1 1 0 0 1 1.414 1.414Z"
          />
        </svg>
        <span class="sr-only">Check icon</span>
      </div>
      <div class="ms-3 text-sm font-normal">Thanks For Taking Part.</div>
      <button
        type="button"
        class="ms-auto -mx-1.5 -my-1.5 bg-white text-gray-400 hover:text-gray-900 rounded-lg focus:ring-2 focus:ring-gray-300 p-1.5 hover:bg-gray-100 inline-flex items-center justify-center h-8 w-8 dark:text-gray-500 dark:hover:text-white dark:bg-gray-800 dark:hover:bg-gray-700"
        data-dismiss-target="#toast-success"
        aria-label="Close"
      >
        <span class="sr-only">Close</span>
        <svg
          class="w-3 h-3"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 14 14"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"
          />
        </svg>
      </button>
    </div>

    <div
      class="absolute inset-0 -z-10 bg-[radial-gradient(45rem_50rem_at_top,theme(colors.indigo.100),white)] opacity-20"
    ></div>
    <div
      class="absolute inset-y-0 right-1/2 -z-10 mr-16 w-[200%] origin-bottom-left skew-x-[-30deg] bg-white shadow-xl shadow-indigo-600/10 ring-1 ring-indigo-50 sm:mr-28 lg:mr-0 xl:mr-16 xl:origin-center"
    ></div>
    <div class="mx-auto max-w-2xl lg:max-w-4xl">
      <img class="mx-auto h-12" :src="filteredArray[0].flag" alt="" />
      <figure v-if="renderGif < 10" class="mt-10">
        <blockquote
          class="text-center text-xl font-semibold leading-8 text-gray-900 sm:text-2xl sm:leading-9"
        >
          <p>
            {{ filteredArray[0].description }}
          </p>
        </blockquote>
        <figcaption class="mt-10">
          <div v-for="(gif, i) in gifs" :key="i">
            <div v-if="gif.id == renderGif">
              <iframe
                class="mx-auto"
                :src="gif.iframe"
                frameborder="0"
              ></iframe>
            </div>
          </div>
          <div class="mt-4 space-x-3 text-base">
            <div class="mb-12">
              <label
                for="large-input."
                class="DescribeText block mb-2 text-sm font-medium text-gray-900 dark:text-white text-center"
                >Please Tell What You Think About This Gif.</label
              >
              <textarea
                v-model="gifDescription"
                type="text"
                id="large-input"
                class="inputField block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
              />
            </div>
          </div>
          <div class="mt-4 flex justify-center">
            <nuxt-link to="/">
              <button
                type="button"
                class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
              >
                Choose Another Nation
              </button>
            </nuxt-link>
            <button
              @click="submitAns"
              type="button"
              class="text-white bg-gray-800 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-800 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700"
            >
              Submit
            </button>
          </div>
        </figcaption>
      </figure>
      <div v-else>
        <p class="thanks flex justify-center">Thanks For Taking part</p>
        <div class="flex justify-center">
          <nuxt-link to="/">
            <button
              type="button"
              class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
            >
              Choose Another Nation
            </button>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- answer -->
    <div class="text-center mt-4">
    </div>
    <div class="flex flex-wrap place-items-center">
      <!-- card -->
      <div
        class="shadow-lg rounded-xl w-72 md:w-96 p-4 bg-white relative overflow-hidden"
     v-for="(ans,i) in renderAns" :key="i" >
        <a href="#" class="w-full h-full block">
          <div class="flex items-center border-b-2 mb-2 py-2">
            <img
              class="w-10 h-10 object-cover rounded-full"
              alt="User avatar"
              :src="ans.country[0].flag"
            />
          </div>
          <div class="w-full">
            <p class="text-gray-800 text-sm font-medium mb-2">
              <iframe :src="ans.gif[0].iframe" frameborder="0"></iframe>
            </p>
            <p class="text-gray-400 text-sm mb-4">
              {{ ans.ans }}
            </p>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
const countries = ref([
  {
    id: "1",
    name: "Thailand",
    flag: "data:image/jpeg;base64,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",
    description: "โปรดอธิบายการกระทำด้านล่างเป็นภาษาไทย",
  },
  {
    id: "2",
    name: "Vietnam",
    flag: "data:image/jpeg;base64,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",
    description: "Vui lòng mô tả hành động dưới đây bằng tiếng Thái bản địa",
  },
  {
    id: "3",
    name: "Philippines",
    flag: "data:image/png;base64,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",
    description: "Pakilarawan ang aksyon sa ibaba sa iyong sariling wika",
  },
  {
    id: "4",
    name: "Indonesia",
    flag: "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAPoAAACnCAMAAAAPIrEmAAAAG1BMVEX/AAD////h4ePjv8H/srLhx8nf0NLh1tj/rKywVIPsAAAAy0lEQVR4nO3PCQGAMAAAoTnd0z+xQTgaMPaL2mMN1KoOqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqououvnfqR7xnxQszqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLqouqi6qLrIrrN+i+9cy5fk87sAAAAASUVORK5CYII=",
    description:
      "Harap jelaskan tindakan di bawah ini ke dalam bahasa ibu Anda",
  },
  {
    id: "5",
    name: "Combodia",
    flag: "data:image/png;base64,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",
    description: "សូមពណ៌នាសកម្មភាពខាងក្រោមជាភាសាកំណើតរបស់អ្នក។",
  },
  {
    id: "6",
    name: "Laos",
    flag: "data:image/jpeg;base64,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",
    description:
      "ກະ​ລຸ​ນາ​ອະ​ທິ​ບາຍ​ການ​ດໍາ​ເນີນ​ການ​ຂ້າງ​ລຸ່ມ​ນີ້​ເປັນ​ພາ​ສາ​ກໍາ​ເນີດ​ຂອງ​ທ່ານ​ເອງ",
  },
]);

const gifs = ref([
  {
    id: 1,
    iframe: "https://giphy.com/embed/3CCXHZWV6F6O9VQ7FL",
  },
  {
    id: 2,
    iframe: "https://giphy.com/embed/2bUpP71bbVnZ3x7lgQ",
  },
  {
    id: 3,
    iframe: "https://giphy.com/embed/8Uxni98XxOdVAIM0x5",
  },
  {
    id: 4,
    iframe: "https://giphy.com/embed/ZXZP0aA6E9noGMLBRO",
  },
  {
    id: 5,
    iframe:
      "https://giphy.com/gifs/flower-happy-birthday-hb-rkoli75BEjGXr7ck4o",
  },
  {
    id: 6,
    iframe: "https://giphy.com/embed/kx6q5Yc79uecw",
  },
  {
    id: 7,
    iframe: "https://giphy.com/embed/3o7TKI7l65d46tJZ7O",
  },
  {
    id: 8,
    iframe: "https://giphy.com/embed/hPTZgtzfRIB5Nfb5rL",
  },
  {
    id: 9,
    iframe: "https://giphy.com/embed/emGHS5TSSDCnk1ekJy",
  },
  {
    id: 10,
    iframe: "https://giphy.com/embed/yW8p4lWql9w2Y",
  },
]);

const renderGif = ref(1);

const ansGif = ref([]);
const gifDescription = ref("");

const description = ref({
  nationid: "",
  gifId: "",
  ans: "",
});

const renderAns = ref([]);

const nationId = ref();
const route = useRoute();
nationId.value = route.params.id;

const nation = ref({});

const filteredArray = countries.value.filter((obj) => obj.id == nationId.value);

const alert = ref(false);
const anscount = ref(false);

const submitAns = () => {
  if (gifDescription.value == "") {
    // tell user that description can't be null
    alert.value = true;
    setTimeout(() => {
      alert.value = false;
    }, 1000);
  } else {
    alert.value = false;
    description.value.ans = gifDescription.value;
    description.value.nationid = nationId.value;
    description.value.gifId = renderGif.value;
    if (renderGif.value > 10) {
      // tell user that gif finish
      anscount.value = true;
    } else {
      gifDescription.value = "";
      renderGif.value++;
    }
  }

  let nation = countries.value.filter((el) => {
    return el.id == nationId.value;
  });

  let gif = gifs.value.filter((el) => {
    return el.id == description.value.gifId;
  });

  renderAns.value.push({
    country: nation,
    gif: gif,
    ans: description.value.ans,
  });


  console.log("tst", renderAns.value)
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400..700&display=swap");
.DescribeText {
  font-size: 1.5rem;
  font-family: "Dancing Script", cursive;
  color: black;
}

.inputField {
  color: black;
}

.thanks {
  font-size: 1.5rem;
  font-family: "Dancing Script", cursive;
  color: black;
}
</style>
