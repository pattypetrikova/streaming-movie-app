<template>
 <div class="home">
   <Hero />

   <div class="container movies">
     <div id="movie-grid" class="movies-grid">
       <div class="movie" v-for="(movie,index) in movies" :key="index">
         <div class="movie-img">
          <img :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" alt="">
           <p class="review">{{ movie.vote_average }}</p>
           <p class="overview"> {{ movie.overview }}</p>
         </div>
         <div class="info">
<!--          slice mi u textu povoli maximalne 25 charakteru , neboli rozdeli od 0 po 25-->
<!--             dale pridame span s '...' jen pokud nazev presahne 25 char.-->
             <p class="title">{{movie.title.slice(0,25) }} <span v-if="movie.title.length > 25">...</span></p>
            <p class="release">Released: {{
                new Date (movie.release_date).toLocaleString('en-us', {
                  month: 'long',
                  day: 'numeric',
                  year: 'numeric',
                })
              }}
            </p>
           <NuxtLink class="button button-light" :to="{name: 'movies-movieid', params: { movieid: movie.id } }">Show more</NuxtLink>
         </div>
       </div>
     </div>
   </div>
 </div>
</template>

<script>
import axios from 'axios'

export default {
 data() {
   return {
     movies: [],
   }
 },
  async fetch() {
   await this.getMovies()
  },
 methods: {
   async getMovies() {
     const data = axios.get(
       `https://api.themoviedb.org/3/movie/now_playing?api_key=37ed43a4f8eaa2abd75f9283692947bc&language=en-US&page=1`)
        const result = await data
       result.data.results.forEach((movie) => {
         this.movies.push(movie)
       })
     console.log(this.movies)
   },
 }
}
</script>

<style lang="scss" scoped>
  .movies {
    padding: 32px 16px;

    .movies-grid {
      display: grid;
      column-gap: 32px;
      row-gap: 64px;
      grid-template-columns: 1fr;
      @media (min-width: 500px) {
        grid-template-columns: repeat(3, 1fr);
      }
      @media (min-width: 750px) {
        grid-template-columns: repeat(2, 1fr);
      }
      @media (min-width: 1100px) {
        grid-template-columns: repeat(4, 1fr);
      }
      .movie {
        position: relative;
        display: flex;
        flex-direction: column;
        .movie-img {
          position: relative;
          overflow: hidden;
          &:hover {
            .overview {
              transform: translateY(0);
            }
          }
          img {
            display: block;
            width: 100%;
            height: 100%;
          }
          .review {
            position: absolute;
            top: 0;
            left: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 40px;
            height: 40px;
            background-color: #c92502;
            color: #fff;
            border-radius: 0 0 16px 0;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
              0 2px 4px -1px rgba(0, 0, 0, 0.06);
          }
          .overview {
            line-height: 1.5;
            position: absolute;
            bottom: 0;
            background-color: rgba($color: #000000, $alpha: 0.7);
            padding: 12px;
            color: #fff;
            transform: translateY(100%);
            transition: 0.3s ease-in-out all;
          }
        }
        .info {
          margin-top: auto;
          .title {
            margin-top: 8px;
            color: #fff;
            font-size: 20px;
          }
          .release {
            margin-top: 8px;
            color: #c9c9c9;
          }
          .button {
            margin-top: 8px;
          }
        }
      }
    }
  }
</style>