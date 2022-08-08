<template>
	<v-app>
	    <v-container>
	      	<v-row>
		        <v-col cols="4">
		        	<v-card >
						  	<v-app-bar
						      	dark
						      	color="primary"
						    >
						      <v-toolbar-title>All</v-toolbar-title>
						      <v-spacer></v-spacer>
						    </v-app-bar> 
						    <v-list>
						      <v-list-item-group>
						 				<draggable v-model="all" group="tasks">
							    		<v-list-item
								          v-for="item in all"
								          :key="item.id"
							        >
							        	<v-list-item-icon>
							            <v-icon v-text="item.icon"></v-icon>
							          </v-list-item-icon>
							        	<v-list-item-content>
							            <v-list-item-title v-text="item.title"></v-list-item-title>
							          </v-list-item-content>
								      </v-list-item>
						  			</draggable>
							    </v-list-item-group>
						    </v-list>
				  		</v-card>
				  	</v-col>

				  	<v-col cols="4">
		        	<v-card >
						  	<v-app-bar
						      	dark
						      	color="primary"
						    >
						      <v-toolbar-title>Vegetables</v-toolbar-title>
						      <v-spacer></v-spacer>
						    </v-app-bar> 
						    <v-list>
						      <v-list-item-group>
						 				<draggable v-model="vegetables" group="tasks" @change="onChangeVegetables">
							    		<v-list-item
								          v-for="item in vegetables"
								          :key="item.id"
							        >
							        	<v-list-item-icon>
							            <v-icon v-text="item.icon"></v-icon>
							          </v-list-item-icon>
							        	<v-list-item-content>
							            <v-list-item-title v-text="item.title"></v-list-item-title>
							          </v-list-item-content>
								      </v-list-item>
						  			</draggable>
							    </v-list-item-group>
						    </v-list>
				  		</v-card>
				  	</v-col>

				  	<v-col cols="4">
		        	<v-card >
						  	<v-app-bar
						      	dark
						      	color="primary"
						    >
						      <v-toolbar-title>Fruits</v-toolbar-title>
						      <v-spacer></v-spacer>
						    </v-app-bar> 
						    <v-list>
						      <v-list-item-group>
						 				<draggable v-model="fruits" group="tasks" @change="onChangeFruits">
							    		<v-list-item
								          v-for="item in fruits"
								          :key="item.id"
							        >
							        	<v-list-item-icon>
							            <v-icon v-text="item.icon"></v-icon>
							          </v-list-item-icon>
							        	<v-list-item-content>
							            <v-list-item-title v-text="item.title"></v-list-item-title>
							          </v-list-item-content>
								      </v-list-item>
						  			</draggable>
							    </v-list-item-group>
						    </v-list>
				  		</v-card>
				  	</v-col>
		    </v-row>
	    </v-container>
  	</v-app>
</template>

<script>
  import draggable from 'vuedraggable'

  	export default {
    	name: 'TodoList',
    	components: {
      	draggable,
      },

    	data: () => ({

		    all: [
		      	{ id: 1, title: "Tomato", icon: "mdi-flag", group: "vegetables" },
		      	{ id: 2, title: "Potato", icon: "mdi-flag", group: "vegetables" },
		      	{ id: 3, title: "Cauliflower", icon: "mdi-flag", group: "vegetables" },
		      	{ id: 4, title: "Onion", icon: "mdi-flag", group: "vegetables" },
		      	{ id: 5, title: "Apple", icon: "mdi-food-apple", group: "fruits" },
		      	{ id: 6, title: "Orange", icon: "mdi-food-apple", group: "fruits" },
		      	{ id: 7, title: "Grapes", icon: "mdi-food-apple", group: "fruits"},
		    ],
		    vegetables: [],
		    fruits: [],
	  	}),
	  	methods: {
	  	  onChangeVegetables(e){
	  	  	if (e.added && e.added.element.group !== 'vegetables') {
	  	  		this.vegetables = this.vegetables.filter(item => item.group === 'vegetables');
	  	  		this.all = [...this.all, e.added.element];
	  	  	}
	  	  },
	  	  onChangeFruits(e){
	  	  	if (e.added && e.added.element.group !== 'fruits') {
	  	  		this.fruits = this.fruits.filter(item => item.group === 'fruits');
	  	  		this.all = [...this.all, e.added.element];
	  	  	}
	  	  },
	  	},
	}
</script>
