# Cookenjoy-
Inspirationene für Frühstück, Mittag- und Abendessen und Backen 
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>cookenjoy</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #fff8f0;
            color: #4d3b2f;
        }

        header {
            background-color: #f5e3d3;
            padding: 20px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        header h1 {
            margin: 0;
            font-size: 2.5em;
        }

        nav {
            margin-top: 10px;
        }

        nav button {
            background-color: #f5e3d3;
            border: none;
            margin: 0 10px;
            padding: 10px 20px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s;
        }

        nav button:hover {
            background-color: #e7d1b8;
        }

        main {
            max-width: 900px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .recipe {
            background-color: #fff0e0;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .recipe img {
            width: 100%;
            border-radius: 10px;
        }

        .recipe h2 {
            color: #c97b63;
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: #f5e3d3;
            margin-top: 40px;
        }

        /* Versteckte Rezepte */
        .hidden {
            display: none;
        }

        /* Suchfeld */
        #search-container {
            text-align: center;
            margin: 20px 0;
        }

        #search-input {
            padding: 10px;
            width: 70%;
            max-width: 400px;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 1em;
        }
    </style>
</head>
<body>

<header>
    <h1>cookenjoy</h1>
    <nav>
        <button onclick="filterRecipes('all')">Alle</button>
        <button onclick="filterRecipes('frühstück')">Frühstück</button>
        <button onclick="filterRecipes('backen')">Backen</button>
    </nav>
</header>

<div id="search-container">
    <input type="text" id="search-input" placeholder="Rezepte durchsuchen..." onkeyup="searchRecipes()">
</div>

<main>
    <section class="recipe" data-category="frühstück">
        <h2>Leckeres Bananen-Pancake-Frühstück</h2>
        <img src="https://images.unsplash.com/photo-1587730905291-5c22cfd1f914?crop=entropy&cs=tinysrgb&fit=max&h=400&w=800" alt="Bananen-Pancakes">
        <p>Starte deinen Morgen mit fluffigen Bananen-Pancakes! Einfach Banane zerdrücken, Eier und Haferflocken dazugeben, in der Pfanne ausbacken und genießen.</p>
    </section>

    <section class="recipe" data-category="backen">
        <h2>Saftiger Zitronen-Muffin</h2>
        <img src="https://images.unsplash.com/photo-1562440499-64b24f88ed37?crop=entropy&cs=tinysrgb&fit=max&h=400&w=800" alt="Zitronen-Muffin">
        <p>Perfekt für den Nachmittag! Saftige Muffins mit frischer Zitrone und einem Hauch Vanille – schnell gemacht und unwiderstehlich lecker.</p>
    </section>

    <section class="recipe" data-category="frühstück">
        <h2>Avocado-Toast mit Ei</h2>
        <img src="https://images.unsplash.com/photo-1584270354949-9bce6c3f45ef?crop=entropy&cs=tinysrgb&fit=max&h=400&w=800" alt="Avocado-Toast">
        <p>Gesundes Frühstück leicht gemacht: Vollkorntoast mit Avocado und Spiegelei. Schnell, lecker und nahrhaft!</p>
    </section>
</main>

<footer>
    <p>© 2025 cookenjoy | Alle Rechte vorbehalten</p>
</footer>

<script>
    function filterRecipes(category) {
        const recipes = document.querySelectorAll('.recipe');
        recipes.forEach(recipe => {
            const matchesCategory = (category === 'all' || recipe.dataset.category === category);
            const matchesSearch = searchMatch(recipe);
            if (matchesCategory && matchesSearch) {
                recipe.classList.remove('hidden');
            } else {
                recipe.classList.add('hidden');
            }
        });
    }

    function searchMatch(recipe) {
        const query = document.getElementById('search-input').value.toLowerCase();
        const title = recipe.querySelector('h2').innerText.toLowerCase();
        const description = recipe.querySelector('p').innerText.toLowerCase();
        return title.includes(query) || description.includes(query);
    }

    function searchRecipes() {
        filterRecipes(document.querySelector('nav button.active')?.dataset.category || 'all');
    }

    // Kategorie-Buttons aktiv markieren
    const buttons = document.querySelectorAll('nav button');
    buttons.forEach(button => {
        button.addEventListener('click', () => {
            buttons.forEach(b => b.classList.remove('active'));
            button.classList.add('active');
            filterRecipes(button.innerText.toLowerCase());
        });
    });

    // Initial alle Rezepte anzeigen
    filterRecipes('all');
</script>

</body>
</html>
