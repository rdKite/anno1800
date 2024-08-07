<template>
  <table>
    <tr v-for="(data, index) in population">
      <td class="whitespace-nowrap">
        <img :src="`src/components/icons/${index}.webp`" :alt="index" class="w-8 inline-block">
        <input
            @change="calculateNeeds()"
            type="text"
            v-model="data.count"
            class="mr-2 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 w-20 p-2.5"
        >
      </td>
      <td
          v-for="(value, name) in consumption"
          @click="toggleNeed(index, name)"
          class="border-gray-300 border-l-2"
      >
        <button v-if="name in data.needs"
            class="need-button rounded-full inline-block w-6 h-6 p-1 pointer"
            :class="{inactive: !data.needs[name].enabled, 'bg-green-400': data.needs[name].basic && data.needs[name].enabled, 'bg-blue-400': !data.needs[name].basic && data.needs[name].enabled, 'bg-red-400': data.needs[name].basic && !data.needs[name].enabled, 'bg-orange-400': !data.needs[name].basic && !data.needs[name].enabled}"
        >
          <img :src="`src/components/icons/${name}.webp`" :alt="name">
        </button>
      </td>
    </tr>
    <tr>
      <td></td>
      <td
          v-for="(amount, need) in consumption"
          class="border-gray-300 border-l-2 text-xs"
      >
        {{ amount }}
      </td>
    </tr>
  </table>
</template>
<script>

export default {
  data() {
    return {
      population: {
        farmers: {
          count: 0,
          needs: {
            fish: {
              basic: true,
              enabled: true,
              supply: 40,
            },
            workClothes: {
              basic: true,
              enabled: true,
              supply: 32.5,
            },
            schnapps: {
              basic: true,
              enabled: true,
              supply: 30,
            },
            soap: {
              basic: false,
              enabled: false,
              supply: 285.71,
            },
            localMail: {
              basic: false,
              enabled: false,
              supply: 62.5,
            },
            regionalMail: {
              basic: false,
              enabled: false,
              supply: 125,
            },
            overseasMail: {
              basic: false,
              enabled: false,
              supply: 333.33,
            },
            flour: {
              basic: false,
              enabled: false,
              supply: 41.67,
            },
            sugar: {
              basic: false,
              enabled: false,
              supply: 83.33,
            },
            jam: {
              basic: false,
              enabled: false,
              supply: 50,
            },
            herbs: {
              basic: false,
              enabled: false,
              supply: 28.82,
            },
            hibiscusPetals: {
              basic: false,
              enabled: false,
              supply: 100,
            },
          },
        },
        workers: {
          count: 0,
          needs: {
            fish: {
              basic: true,
              enabled: true,
              supply: 20,
            },
            workClothes: {
              basic: true,
              enabled: true,
              supply: 16.25,
            },
            schnapps: {
              basic: true,
              enabled: true,
              supply: 15,
            },
            sausages: {
              basic: true,
              enabled: true,
              supply: 50,
            },
            bread: {
              basic: true,
              enabled: true,
              supply: 55,
            },
            soap: {
              basic: true,
              enabled: true,
              supply: 120,
            },
            beer: {
              basic: true,
              enabled: true,
              supply: 65,
            },
            rum: {
              basic: false,
              enabled: false,
              supply: 50,
            },
            highWheeler: {
              basic: false,
              enabled: false,
              supply: 125,
            },
            localMail: {
              basic: false,
              enabled: false,
              supply: 30.77,
            },
            regionalMail: {
              basic: false,
              enabled: false,
              supply: 125,
            },
            overseasMail: {
              basic: false,
              enabled: false,
              supply: 133.3,
            },
            hotSauce: {
              basic: false,
              enabled: false,
              supply: 100,
            },
            beef: {
              basic: false,
              enabled: false,
              supply: 80,
            },
            soccerBalls: {
              basic: false,
              enabled: false,
              supply: 100,
            },
            clayPipes: {
              basic: false,
              enabled: false,
              supply: 150,
            },
          },
        },
        artisans: {
          count: 0,
          needs: {
            sausages: {
              basic: true,
              enabled: true,
              supply: 25,
            },
            bread: {
              basic: true,
              enabled: true,
              supply: 27.5,
            },
            soap: {
              basic: true,
              enabled: true,
              supply: 60,
            },
            beer: {
              basic: true,
              enabled: true,
              supply: 32.5,
            },
            cannedFood: {
              basic: true,
              enabled: true,
              supply: 97.5,
            },
            sewingMachines: {
              basic: true,
              enabled: true,
              supply: 35,
            },
            furCoats: {
              basic: true,
              enabled: true,
              supply: 37.5,
            },
            rum: {
              basic: true,
              enabled: true,
              supply: 17.5,
            },
            soccerBalls: {
              basic: false,
              enabled: false,
              supply: 50,
            },
            wool: {
              basic: false,
              enabled: false,
              supply: 16.67,
            },
            clay: {
              basic: false,
              enabled: false,
              supply: 12.5,
            },
            paper: {
              basic: false,
              enabled: false,
              supply: 33.33,
            },
            perfumes: {
              basic: false,
              enabled: false,
              supply: 133.33,
            },
            scooter: {
              basic: false,
              enabled: false,
              supply: 153.85,
            },
          },
        },
        engineers: {
          count: 0,
          needs: {
            cannedFood: {
              basic: true,
              enabled: true,
              supply: 48.75,
            },
            sewingMachines: {
              basic: true,
              enabled: true,
              supply: 17.5,
            },
            furCoats: {
              basic: true,
              enabled: true,
              supply: 18.75,
            },
            rum: {
              basic: true,
              enabled: true,
              supply: 8.75,
            },
            glasses: {
              basic: true,
              enabled: true,
              supply: 112.5,
            },
            coffee: {
              basic: true,
              enabled: true,
              supply: 21.25,
            },
            lightBulb: {
              basic: true,
              enabled: true,
              supply: 80,
            },
            highWheeler: {
              basic: true,
              enabled: true,
              supply: 40,
            },
            pocketWatch: {
              basic: true,
              enabled: true,
              supply: 127.5,
            },
            chewingGum: {
              basic: true,
              enabled: false,
              supply: 192.31,
            },
            typewriters: {
              basic: true,
              enabled: false,
              supply: 125,
            },
            violins: {
              basic: true,
              enabled: false,
              supply: 333.33,
            },
            soap: {
              basic: false,
              enabled: false,
              supply: 32,
            },
            chocolate: {
              basic: false,
              enabled: false,
              supply: 66.67,
            },
            shampoo: {
              basic: false,
              enabled: false,
              supply: 55.56,
            },
            mezcal: {
              basic: false,
              enabled: false,
              supply: 66.67,
            },
            iceCream: {
              basic: false,
              enabled: false,
              supply: 50,
            },
            medicine: {
              basic: false,
              enabled: false,
              supply: 60,
            },
          },
        },
        investors: {
          count: 0,
          needs: {
            glasses: {
              basic: true,
              enabled: true,
              supply: 56.25,
            },
            coffee: {
              basic: true,
              enabled: true,
              supply: 10.625,
            },
            lightBulb: {
              basic: true,
              enabled: true,
              supply: 40,
            },
            highWheeler: {
              basic: true,
              enabled: true,
              supply: 20,
            },
            pocketWatch: {
              basic: true,
              enabled: true,
              supply: 63.75,
            },
            chewingGum: {
              basic: true,
              enabled: false,
              supply: 181.82,
            },
            typewriters: {
              basic: true,
              enabled: false,
              supply: 71.43,
            },
            violins: {
              basic: true,
              enabled: false,
              supply: 314.47,
            },
            biscuits: {
              basic: true,
              enabled: false,
              supply: 37.31,
            },
            cognac: {
              basic: true,
              enabled: false,
              supply: 90.91,
            },
            billiardTables: {
              basic: true,
              enabled: false,
              supply: 76.92,
            },
            toys: {
              basic: true,
              enabled: false,
              supply: 178.57,
            },
            furs: {
              basic: false,
              enabled: false,
              supply: 62.5,
            },
            bearFur: {
              basic: false,
              enabled: false,
              supply: 153.85,
            },
            tapestries: {
              basic: false,
              enabled: false,
              supply: 62.5,
            },
            perfumes: {
              basic: false,
              enabled: false,
              supply: 80,
            },
            fans: {
              basic: false,
              enabled: false,
              supply: 66.67,
            },
            filmReel: {
              basic: false,
              enabled: false,
              supply: 88.89,
            },
          },
        },
      },
      consumption: {
        fish: 0,
        workClothes: 0,
        schnapps: 0,
        sausages: 0,
        bread: 0,
        soap: 0,
        beer: 0,
        cannedFood: 0,
        sewingMachines: 0,
        furCoats: 0,
        rum: 0,
        glasses: 0,
        coffee: 0,
        lightBulb: 0,
        highWheeler: 0,
        pocketWatch: 0,
        chewingGum: 0,
        biscuits: 0,
        cognac: 0,
        typewriters: 0,
        billiardTables: 0,
        violins: 0,
        toys: 0,
        localMail: 0,
        regionalMail: 0,
        overseasMail: 0,
        flour: 0,
        sugar: 0,
        jam: 0,
        herbs: 0,
        hibiscusPetals: 0,
        hotSauce: 0,
        beef: 0,
        soccerBalls: 0,
        clayPipes: 0,
        wool: 0,
        clay: 0,
        paper: 0,
        perfumes: 0,
        scooter: 0,
        chocolate: 0,
        shampoo: 0,
        mezcal: 0,
        iceCream: 0,
        medicine: 0,
        furs: 0,
        bearFur: 0,
        tapestries: 0,
        fans: 0,
        filmReel: 0,
      },
    }
  },
  methods: {
    toggleNeed(popTier, need) {
      this.population[popTier].needs[need].enabled = !this.population[popTier].needs[need].enabled;
      this.calculateNeed(need);
    },
    calculateNeeds() {
      for (let index in this.consumption) {
        this.calculateNeed(index);
      }
    },
    calculateNeed(need) {
      let value = 0;
      for (let index in this.population) {
        let data = this.population[index];
        let needData = data.needs[need];
        if (needData && needData.enabled) {
          value += data.count / needData.supply;
        }
      }
      value = Math.ceil(value * 10) / 10;
      this.consumption[need] = value;
    }
  }
};
</script>

<style scoped>
.need-button.inactive {
  opacity: 0.5;
}

.need-button.disabled {
  opacity: 0.1;
  cursor: default;
}
</style>