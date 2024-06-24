<template>
  <main>
    <section>
      <h2 class="title">Pentagon</h2>
      <ThePentagon :imgPath="picture" />
    </section>

    <section class="flex">
      <h2 class="title">Flex-box</h2>
      <ThePentagon :imgPath="pictureList" />
      <button class="btn btn-primary m-3" @click="randomSort">Случайная сортировка</button>
    </section>

    <section class="grid">
      <h2 class="title">Grid</h2>
      <ThePentagon :imgPath="pictureList" />
      <button class="btn btn-primary m-3" @click="randomSort">Случайная сортировка</button>
    </section>

    <section>
   
      <h2 class="title">Bootstrap</h2>
      <ThePentagon :imgPath="pictureList" :type="'bootstrap'" />
      <button class="btn btn-primary m-3" @click="randomSort">Случайная сортировка</button>
    </section>
    
  </main>
</template>

<script>
export default {
  data() {
    return {
      picture: [],
      pictureList: [],
    }
  },
  async mounted() {
    const pictureNew = [];
    const pictureListNew = [];
    pictureNew.push(
      {
        img: (await import("@/assets/img/item1.jpg")).default,
      },
    );
    pictureListNew.push(
      {
        img: (await import("@/assets/img/item1.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item2.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item3.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item4.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item5.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item6.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item7.jpg")).default,
      },
      {
        img: (await import("@/assets/img/item5.jpg")).default,
      }
    );
    this.picture = pictureNew;
    this.pictureList = pictureListNew;
  },
  methods: {
    randomSort() {
      let m = this.pictureList.length, t, i;
      while (m) {
        i = Math.floor(Math.random() * m--);
        t = this.pictureList[m];
        this.pictureList[m] = this.pictureList[i];
        this.pictureList[i] = t;
      }
    }
  }
}
</script>

<style lang="scss">
.flex {
  .pentagon {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin: 0 -1rem;
    &__item {
      padding: 1rem;
      @media(min-width: 420px)  {
        flex: 0 0 100%;
        max-width: 100%;
      }
      @media(min-width: 720px) and (max-width: 1099px) {
        flex: 0 0 50%;
        max-width: 50%;
      }
      @media(min-width: 1100px) and (max-width: 1599px) {
        flex: 0 0 33.333%;
        max-width: 33.333%;
      }
      @media(min-width: 1600px) {
        flex: 0 0 25%;
        max-width: 25%;
      }
    }
  }
}
.grid {
  .pentagon {
    display: grid;
    gap: 1rem;
    @media(min-width: 420px)  {
      grid-template-columns: 1fr;
      }
      @media(min-width: 720px) and (max-width: 1099px) {
        grid-template-columns: repeat(2, 1fr);
      }
      @media(min-width: 1100px) and (max-width: 1599px) {
        grid-template-columns: repeat(3, 1fr);
      }
      @media(min-width: 1600px) {
        grid-template-columns: repeat(4, 1fr);
      }
  }
}
</style>