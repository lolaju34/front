<!-- App.svelte -->
<script>
    import { onMount } from 'svelte';
    import FilmList from './lib/FilmList.svelte'; // Importez FilmList.svelte
  
    let films = [];
  
    const generateFilms = async () => {
      try {
        const response = await fetch('http://localhost:3000/api/films/generate');
        if (response.ok) {
          films = await response.json();
        } else {
          console.error('Erreur lors de la récupération des films.');
        }
      } catch (error) {
        console.error('Erreur lors de la récupération des films:', error);
      }
    };
  </script>
  
  <main>
    <h1>Génération de films aléatoires</h1>
    <button on:click={generateFilms}>Générer des films</button>
    <!-- Utilisez FilmList.svelte pour afficher les films -->
    <FilmList {films} />
  </main>
  