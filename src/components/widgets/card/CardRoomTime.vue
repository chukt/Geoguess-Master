<template>
  <v-card color="#061422">
    <v-card-title>
      <span id="card-title">{{ $t('CardRoomTime.title') }}</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col 
            cols="6"
            sm="4"
            md="4"
            lg="4"
            xl="4">
            <v-select
              dark 
              v-model="timeLimitation"
              :items="timeLimitationItems"></v-select>
          </v-col>          
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions>
      <div class="flex-grow-1"></div>
      <v-btn
        dark
        depressed
        color="#43B581"
        @click="setTimeLimitation">{{ $t('CardRoomTime.next') }}</v-btn>
      <v-btn
        dark
        depressed
        color="#FF5252"
        @click="cancel">{{ $t('CardRoomTime.cancel') }}</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
  import Vue from 'vue'

  import { TranslateResult } from 'vue-i18n'

  declare interface timeLimitationItem {
    text: string | TranslateResult,
    value: number,
  }

  export type DataType = {
    timeLimitation: number,
    timeLimitationItems: timeLimitationItem[],
  }

  export default Vue.extend({
    name: 'CardRoomTime',

    data(): DataType {
      return {
        timeLimitation: 0,
        timeLimitationItems: [
          {
            text: this.$t('CardRoomTime.infinite'),
            value: 0,
          },
          {
            text: '1',
            value: 1,
          },
          {
            text: '2',
            value: 2,
          },
          {
            text: '3',
            value: 3,
          },
          {
            text: '4',
            value: 4,
          },
          {
            text: '5',
            value: 5,
          }, 
          {
            text: '6',
            value: 6,
          },
          {
            text: '7',
            value: 7,
          },
          {
            text: '8',
            value: 8,
          },
          {
            text: '9',
            value: 9,
          },
          {
            text: '10',
            value: 10,
          },          
        ],
      }
    },

    methods: {
      setTimeLimitation() {
        this.$emit('setTimeLimitation', this.timeLimitation)
      },

      cancel() {
        this.$emit('cancel')
      },    
    }
  })
</script>

<style scoped>
  #card-title {
    font-size: 16px;
    font-weight: 500;
    color: #FFFFFF;
    opacity: 0.9;
  } 
</style>