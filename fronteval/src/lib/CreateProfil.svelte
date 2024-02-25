<script>
    let profileNumber = ''; // Initialisez la variable profileNumber
    let filmButtonVisible = false; // Ajoutez une variable pour contrôler la visibilité du bouton de génération de films

    async function createUserProfile() {
        try {
            const response = await fetch('http://localhost:3000/api/user/profile', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ profileNumber })
            });

            if (response.ok) {
                const data = await response.json();
                alert(data.message); // Affichez le message de succès retourné par le serveur
                filmButtonVisible = true; // Définissez la visibilité du bouton sur true après la création réussie du profil
            } else {
                const { message } = await response.json();
                throw new Error(message); // Lancez une erreur pour la capturer dans le bloc catch
            }
        } catch (error) {
            console.error('Erreur lors de la création du profil utilisateur:', error);
            alert('Erreur lors de la création du profil utilisateur: ' + error.message);
        }
    }

    async function generateFilms() {
        // Ajoutez la logique pour générer des films ici
        // Cette fonction sera appelée lorsque le bouton de génération de films est cliqué
    }
</script>

<main>
    <h1>Créer un profil utilisateur</h1>
    <input type="number" bind:value={profileNumber} placeholder="Numéro de profil" />
    <button on:click={createUserProfile}>Créer</button>
    {#if filmButtonVisible}
        <button on:click={generateFilms}>Générer des films</button> <!-- Ajoutez le bouton de génération de films -->
    {/if}
</main>
