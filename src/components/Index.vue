//Index.vue

<template>
  <div>
    <h1>My Post App</h1>
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <!-- Bootstrap CSS 5.1-->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css" rel="stylesheet" 
        integrity="sha384-KyZXEAg3QhqLMpG8r+8fhAXLRk2vvoC2f3B09zVXn8CA5QIVfZOJ3BCsw2P0p/We" crossorigin="anonymous
        ">
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" 
        integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous
        ">
        
    </head>
     <body>
        <div class="container mt-4" id="app">
            <table class="table table-bordered">
               
            <thead>
            <tr>
                <th scope="col">UserId</th>
                <th scope="col">Id</th>
                <th scope="col">Title</th>
                <th scope="col">Body</th>
                

            </tr>
            </thead>
            <tbody>
            <tr v-for="PostData in PostDataList" :key="PostData.id" class="Post-data">
                <td scope="col">{{ PostData.userId }}</td>

                <td scope="col">{{ PostData.id }}</td>
                <td scope="col">{{ PostData.title }}</td>
                <td scope="col">{{ PostData.body }}</td>

            </tr>
            
            </tbody>
            </table>
        <button v-on:click="getPostData">Get Post Data</button>
        </div>
    

    

      </body>
  </div>
</template>

<script>
export default {
  name: "Post",
  data() {
    return {
      PostDataList: []
    };
  },
  methods: {
    getPostData() {
      fetch("https://jsonplaceholder.typicode.com/posts")
        .then(response => response.json())
        .then(data => (this.PostDataList = data));
    }
  }
};
</script>

<style>
button {
    padding:10px;
    background-color: #1aa832;
    color: white;
    border: 1px solid #ccc;
}
</style>