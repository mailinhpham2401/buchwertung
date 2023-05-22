<template>
  <div class="container">
    <h1 class="title">Book Reviews</h1>
    <form @submit.prevent="submitReview" class="form">
      <div class="form-group">
        <label for="bookTitle">Titel:</label>
        <input type="text" id="bookTitle" v-model="newReview.title" required>
      </div>
      <div class="form-group">
        <label for="bookAuthor">Autor:</label>
        <input type="text" id="bookAuthor" v-model="newReview.author" required>
      </div>
      <div class="form-group">
        <label for="rating">Rating:</label>
        <select id="rating" v-model="newReview.rating" required>
          <option value="" disabled selected>Select rating</option>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
          <option value="5">5</option>
        </select>
      </div>
      <div class="form-group">
        <label for="reviewText">Bewertung:</label>
        <textarea id="reviewText" v-model="newReview.text" required></textarea>
      </div>
      <div class="form-group">
        <button type="submit" class="submit-btn">Absenden</button>
      </div>
    </form>
    <div class="reviews">
      <h2 class="subtitle">Bewertungen:</h2>
      <div v-for="review in reviews" :key="review.id" class="review">
        <h3 class="review-title">{{ review.title }}</h3>
        <p class="review-author">Von: {{ review.author }}</p>
        <p class="review-rating">Rating: {{ review.rating }}</p>
        <p class="review-text">{{ review.text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newReview: {
        title: '',
        author: '',
        rating: null,
        text: ''
      },
      reviews: []
    };
  },
  methods: {
    submitReview() {
      const review = { ...this.newReview };
      this.reviews.unshift(review);
      this.newReview.title = '';
      this.newReview.author = '';
      this.newReview.rating = null;
      this.newReview.text = '';
    }
  }
};
</script>

<style>
.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    font-family: Arial, Helvetica, sans-serif;
  }
  
  .title {
    font-size: 32px;
    text-align: center;
    margin-bottom: 30px;
    color: #333;
  }
  
  .form {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 10px;
    font-weight: bold;
    color: #555;
  }
  
  input[type="text"],
  textarea,
  select {
    width: 90%;
    padding: 12px;
    border-radius: 5px;
    border: 1px solid #ccc;
    font-size: 16px;
  }
  
  select {
    appearance: none;
    background-color: #fff;
    cursor: pointer;
  }
  
  .submit-btn {
    padding: 12px 24px;
    background-color: #007bff;
    border: none;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s ease;
  }
  
  .submit-btn:hover {
    background-color: #0056b3;
  }
  
  .reviews {
    margin-top: 30px;
  }
  
  .subtitle {
    font-size: 24px;
    margin-bottom: 20px;
    color: #333;
  }
  
  .review {
    border: 1px solid #ccc;
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    background-color: #fff;
    transition: box-shadow 0.3s ease;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .review:hover {
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .review-title {
    font-size: 22px;
    margin-bottom: 10px;
    color: #333;
  }
  
  .review-author {
    font-style: italic;
    margin-bottom: 10px;
    color: #555;
  }
  
  .review-rating {
    font-weight: bold;
    margin-bottom: 10px;
    color: #007bff;
  }
  
  .review-text {
    margin-bottom: 0;
    color: #333;
  }
  
  @media screen and (max-width: 600px) {
    .container {
      padding: 10px;
    }
  
    .title {
      font-size: 24px;
      margin-bottom: 20px;
    }
  
    .form {
      padding: 10px;
    }
  
    input[type="text"],
    textarea,
    select {
      font-size: 14px;
    }
  
    .submit-btn {
      font-size: 14px;
    }
  
    .review-title {
      font-size: 18px;
    }
  
    .review {
      padding: 10px;
      margin-bottom: 10px;
    }
  }
</style>
