<template>
  <div id="web">
    <v-carousel
        cycle
        height="600px"
        hide-delimiter-background
        show-arrows-on-hover
    >
        <v-carousel-item
            v-for="(slide, i) in slides"
            :key="i"
        >
            <v-sheet
                :color="colors[i]"
                height="100%"
            >
                <v-row
                class="fill-height"
                align="center"
                justify="center"
                >
                <div class="text-h2">
                    {{ slide }} Slide
                </div>
                </v-row>
            </v-sheet>
        </v-carousel-item>
    </v-carousel>
    <div class="news">
        <h2>ニュース</h2>
        <v-btn value="left" text>
            一覧を見る
        </v-btn>

        <br>

        <v-btn-toggle
            v-model="text"
            tile
            color="deep-purple accent-3"
            group
        >
            <v-btn value="all">
                すべて
            </v-btn>

            <v-btn value="pressReleases">
                プレスリリース
            </v-btn>

            <v-btn value="media">
                メディア掲載
            </v-btn>

            <v-btn value="awards">
                アワード賞
            </v-btn>
        </v-btn-toggle>
        <div class="news-boxs">
            <v-row>
                <v-flex
                    v-for="newsContet in newsContets"
                    :key="newsContet.created"
                    xs6
                    md4
                    lg3
                >
                <v-slide-x-transition>
                    <v-card class="ma-2" to="/">
                        <v-img
                            :src="newsContet.img"
                            class="mx-4 mb-4"
                            border
                            width="80%"
                        ></v-img>
                        <v-card-text>
                            {{newsContet.text}}
                            <div class="my-1 text-subtitle-4">
                                {{newsContet.category}}
                            </div>
                            <div class="text-subtitle-4">
                                {{newsContet.created}}
                            </div>
                        </v-card-text>
                    </v-card>
                </v-slide-x-transition>
                </v-flex>
            </v-row>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    data: () => ({
      colors: [
          'indigo',
          'warning',
          'pink darken-2',
          'red lighten-1',
          'deep-purple accent-4',
        ],
        slides: [
          'First',
          'Second',
          'Third',
          'Fourth',
          'Fifth',
        ],
        text: 'all',
        loading: false,
        selection: 1,
        newsContets:[
            {
                img:"/images/thumb_raksul.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月10日",
                to:""
            },
            {
                img:"/images/thumb_press.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"アワード賞",
                created:"2022年10月11日",
                to:""
            },
            {
                img:"/images/thumb_novasell.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月12日",
                to:""
            },
            {
                img:"/images/thumb_media.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"メディア掲載",
                created:"2022年10月13日",
                to:""
            },
            {
                img:"/images/thumb_raksul.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月10日",
                to:""
            },
            {
                img:"/images/thumb_press.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"アワード賞",
                created:"2022年10月11日",
                to:""
            },
            {
                img:"/images/thumb_novasell.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月12日",
                to:""
            },
            {
                img:"/images/thumb_media.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"メディア掲載",
                created:"2022年10月13日",
                to:""
            },
            {
                img:"/images/thumb_raksul.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月10日",
                to:""
            },
            {
                img:"/images/thumb_press.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"アワード賞",
                created:"2022年10月11日",
                to:""
            },
            {
                img:"/images/thumb_novasell.png",
                text:"＜ラクスル×ワタミ＞OMOマーケティングの成功パターンを探る実証実験第二弾ポスティング前に認知獲得しておくことでチラシの反響が約2.8倍に向上",
                category:"プレスリリース",
                created:"2022年10月12日",
                to:""
            },
            {
                img:"/images/thumb_media.png",
                text:"IT業務を自動化を可能とするプラットフォームを運営する、ラクスルグループのジョーシス株式会社は、ベンチャーキャピタル等から総額44億円の資金を調達。",
                category:"メディア掲載",
                created:"2022年10月13日",
                to:""
            },
        ]
    }),
    methods: {
      reserve () {
        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
    },
}
</script>

<style>

</style>