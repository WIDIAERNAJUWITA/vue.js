<template>
  <div>
    <!-- template categries -->
    <v-container class="ma-0 pa-0" grid-list-sm>
      <div class="text-right">
        <v-btn small text to="/categories" class="blue--text">
          All Categories <v-icon>mdi-chevron-right</v-icon>
        </v-btn>
      </div> 
      <v-layout wrap>
        <v-flex v-for="(category) in categories" :key="`category-`+category.id" xs6>
          <v-card :to="'/category/'+ category.slug">
            <v-img
              :src="category.image"
              class="white--text"
            >
              <v-card-title 
                class="fill-height align-end"
                v-text="category.name"
              ></v-card-title>
            </v-img>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>

    <!-- template books -->

  </div>
</template>
<script>

export default {
  data: () => ({
    categories: [
      { 
        id: 1,
        image: 'https://via.placeholder.com/150',
        name: 'Ekonomi',
        slug: 'ekonomi'
      },
      { 
        id: 2,
        image: 'https://via.placeholder.com/150',
        name: 'Agama',
        slug: 'agama'
      },
    ]
  })
};
</script>
