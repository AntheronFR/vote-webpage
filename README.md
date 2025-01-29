<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>À la recherche du nouveau nom</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            max-width: 600px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 8px;
        }
        h1 {
            font-size: 24px;
            text-align: center;
        }
        .checkbox-group {
            margin: 20px 0;
        }
        button {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>À la recherche du nouveau nom</h1>
    <p>Merci pour vos propositions ! Il est temps de voter pour vos deux préférées.<br>
       Si vous avez formulé plusieurs idées, vous pouvez voter pour l'une de vos propositions et votre second vote devra aller à celle d'une autre personne, ou voter pour deux propositions d'une autre personne.</p>
    
    <div class="checkbox-group">
        <p><strong>Les propositions de l'équipe (2 votes)</strong></p>
        <label><input type="checkbox" name="vote" value="Bloom"> Bloom (floraison = croissance)</label><br>
        <label><input type="checkbox" name="vote" value="Content Studio"> Content Studio</label><br>
        <label><input type="checkbox" name="vote" value="Spark"> Spark (l'étincelle qui initie quelque chose de plus grand)</label><br>
        <label><input type="checkbox" name="vote" value="Node"> Node (nœud, intersection, point de connexion entre les contenus, les formats, les plateformes)</label><br>
        <label><input type="checkbox" name="vote" value="Fuse"> Fuse (la fusion/connexion entre les contenus et les plateformes)</label><br>
    </div>

    <button onclick="submitVote()">Soumettre</button>

    <script>
        const checkboxes = document.querySelectorAll('input[type="checkbox"]');
        
        checkboxes.forEach((checkbox) => {
            checkbox.addEventListener('change', () => {
                const checkedBoxes = document.querySelectorAll('input[type="checkbox"]:checked');
                
                if (checkedBoxes.length >= 2) {
                    // Désactiver les cases non cochées
                    checkboxes.forEach((cb) => {
                        if (!cb.checked) {
                            cb.disabled = true;
                        }
                    });
                } else {
                    // Réactiver toutes les cases si moins de 2 cochées
                    checkboxes.forEach((cb) => {
                        cb.disabled = false;
                    });
                }
            });
        });

        function submitVote() {
            const selected = Array.from(document.querySelectorAll('input[type="checkbox"]:checked')).map(cb => cb.value);
            if (selected.length !== 2) {
                alert("Veuillez sélectionner exactement 2 options avant de soumettre.");
                return;
            }
            alert("Votre vote a été soumis : " + selected.join(", "));
        }
    </script>
</body>
</html>
