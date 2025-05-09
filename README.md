# Take-Home Exercise: Movie Explorer

## Project Overview
The **Movie Explorer** is a Vue.js 3 and Nuxt.js-based web application that allows users to search for movies using the **TMDB (The Movie Database) API**, view detailed movie information, and manage a personal list of favorite movies. This exercise tests your skills in modern JavaScript, Vue.js 3 fundamentals, Composition API, state management, routing, form handling, testing, and best practices in accessibility and performance optimization.

---

## Functional Requirements

### 1. Search Functionality
- **Feature**: Provide a multi-field search form where users can input queries by title, year, or genre.
- **Behavior**: 
  - On submission, fetch a list of movies from the TMDB API based on the provided inputs.
  - Display search results in a responsive grid or list format.
- **Display**: Each movie should show:
  - Title
  - Release year
  - Poster image (thumbnail)
  - Overview (if available)
  - Rating

### 2. Movie Details
- **Feature**: Allow users to click on a movie to view more detailed information.
- **Implementation**:
  - Use a dedicated details page accessible via a unique URL (e.g., `/movie/:id`).
  - Optionally, implement a modal overlay as an alternative.
- **Optimization**: Use **dynamic imports** (e.g., Nuxt.js's `defineAsyncComponent` or `<LazyComponent>`) to lazy load the details view for performance.

### 3. Favorites Management
- **Feature**: Enable users to add and remove movies from a "favorites" list.
- **State Management**: Use a global state solution such as:
  - **Pinia** (preferred for Vue 3)
  - **Vuex**
  - **Nuxt's built-in state management** with `useState` composable
- **Display**: Provide a dedicated page (e.g., `/favorites`) to view all favorite movies.

### 4. Routing and Navigation
- **Feature**: Implement client-side routing using **Vue Router** (or Nuxt.js built-in routing).
- **Routes**:
  - `/`: Search page with the search form and results.
  - `/movie/:id`: Movie details page for a specific movie.
  - `/favorites`: Page displaying the user's favorite movies.
- **Navigation**: Include a navigation bar or menu with links to the **Search** and **Favorites** pages.

### 5. Form Handling
- **Feature**: Implement a search form with multiple fields (title, year, genre) and validation.
- **Behavior**:
  - Ensure at least one field is filled before allowing submission.
  - Display user-friendly error messages for invalid submissions.
- **Optional Enhancement**: Add a form to allow users to attach ratings or notes when adding a movie to favorites.

### 6. User Interface & Experience
- **Responsiveness**: Ensure the application is fully responsive and works on mobile, tablet, and desktop devices.
- **Accessibility**: Use **semantic HTML** and include proper **ARIA attributes** to meet accessibility standards.
- **Styling**: Use CSS (or a CSS-in-JS solution like Vue's `<style scoped>` or Nuxt's module) with attention to maintainability and scalability.

---

## Technical Requirements

### 1. Modern Vue.js 3 & JavaScript
- Use the **Composition API** with `<script setup>` syntax for most components.
- Implement common composables using Vue 3 reactivity system (e.g., `ref`, `reactive`, `computed`, `watch`).
- Write clean, modular, and well-documented code using **ES6+** features.

### 2. Vue Router / Nuxt.js Routing
- Implement routing with at least three routes: `/`, `/movie/:id`, and `/favorites`.
- If using Nuxt.js, leverage the file-based routing system with the `pages/` directory.
- Ensure proper navigation between pages using `<NuxtLink>` or `<RouterLink>`.

### 3. Form Handling
- Use Vue's two-way binding (`v-model`) to manage form state.
- Implement form validation to ensure at least one search field is filled.
- Handle form submissions and integrate with the TMDB API.

### 4. Optional: TypeScript
- You may choose to use **TypeScript** to add type safety to your application. (This is optional but considered a plus.)

### 5. Build Tools & Project Setup
- Set up the project using a modern build toolchain:
  - **Nuxt.js 3** (preferred)
  - **Vite** with Vue 3
  - **Vue CLI**
- Ensure that the project can be built and served locally with clear instructions.

### 6. Testing
- Write **unit and integration tests** using **Vitest**, **Jest**, or **Vue Test Utils**.
- Test critical components, including:
  - Search form (validation and submission)
  - Routing (navigation between pages)
  - Favorites functionality (adding/removing movies)
- Aim for good test coverage to demonstrate a commitment to code quality.

### 7. Performance Optimization
- Implement performance optimizations where applicable:
  - Use **memoization** (e.g., `computed` properties) to avoid unnecessary re-renders.
  - Apply **code-splitting** via dynamic imports for lazy loading components.
  - Implement proper caching strategies for API calls.
- Document any performance considerations in your README.

### 8. Version Control & Documentation
- Use **Git** for version control and commit your work in a logical, well-documented manner.
- Provide a **README.md** file that includes:
  - A brief overview of the project.
  - Instructions on how to set up, run, and test the application.
  - An explanation of your approach to routing, form handling, state management, and any trade-offs made.

---

## How to Use the TMDB API

### Overview
The **TMDB API** allows you to search for movies and retrieve their details. In this project, it will be used to power the search functionality by fetching movie data based on user queries.

### API Endpoint
- **Base URL**: `https://api.themoviedb.org/3`
- **Search Endpoint**: `/search/movie?api_key={your_api_key}&query={searchQuery}`
- **Movie Details**: `/movie/{movie_id}?api_key={your_api_key}`

### Key Parameters
- **`api_key`**: Required. You'll need to sign up for a free TMDB API key.
- **`query`**: Required search query for the search endpoint.
- **`year`**: Optional, filter by release year.
- **`with_genres`**: Optional, filter by genre ID.
- **`page`**: Optional, for pagination (default: 1).

### Response Structure
The API returns a JSON object with a list of movie items under the `results` key. Each item includes:
- **`id`**: Unique movie identifier.
- **`title`**: Movie title.
- **`release_date`**: Release date.
- **`overview`**: Brief summary.
- **`poster_path`**: Partial URL for the poster image (needs to be combined with base image URL).
- **`vote_average`**: Average rating.

**Example Response**:
```json
{
  "results": [
    {
      "id": 123456,
      "title": "The Matrix",
      "release_date": "1999-03-31",
      "overview": "A computer hacker learns about the true nature of reality...",
      "poster_path": "/f89U3ADr1oiB1s9GkdPOEpXUk5H.jpg",
      "vote_average": 8.1
    }
  ]
}
```

### Getting Images
- **Base Image URL**: `https://image.tmdb.org/t/p/`
- **Size Options**: `w92`, `w154`, `w185`, `w342`, `w500`, `w780`, `original`
- **Full Image URL**: `https://image.tmdb.org/t/p/w500/f89U3ADr1oiB1s9GkdPOEpXUk5H.jpg`

---

## Evaluation Criteria

Your submission will be evaluated based on:

1. **Code Quality**: Clean, maintainable, and well-structured code following Vue.js best practices.
2. **Vue.js 3 Knowledge**: Effective use of the Composition API, components, directives, and Vue's reactivity system.
3. **Nuxt.js Implementation**: Proper utilization of Nuxt.js features if chosen as the framework.
4. **State Management**: Proper implementation of global state for favorites management.
5. **Routing**: Correct implementation of Vue Router or Nuxt.js routing.
6. **Form Handling**: Clean implementation of forms with proper validation.
7. **Performance**: Thoughtful application of performance optimizations.
8. **Testing**: Comprehensive testing of critical functionality.
9. **Documentation**: Clear, concise documentation of your approach and setup instructions.

---

## Submission Guidelines

1. Create a new GitHub repository for your submission.
2. Implement the Movie Explorer application according to the requirements.
3. Include a README.md with setup instructions and explanation of your approach.
4. Commit your code regularly with meaningful commit messages.
5. Submit the repository URL by [submission deadline].

Good luck!
