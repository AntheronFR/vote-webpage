<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>À la recherche du nouveau nom</title>
    <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script>
        (function () {
            // Initialise EmailJS avec ton user ID
            emailjs.init("TON_PUBLIC_KEY"); // Remplace par ta clé publique EmailJS
        })();

        function submitVote() {
            const selected = Array.from(document.querySelectorAll('input[type="checkbox"]:checked')).map(cb => cb.value);
            if (selected.length < 1 || selected.length > 2) {
                alert("Veuillez sélectionner une ou deux options avant de soumettre.");
                return;
            }

            // Préparer les données pour l'e-mail
            const templateParams = {
                votes: selected.join(", "), // Combine les votes en une chaîne
                date: new Date().toLocaleString(), // Ajoute la date de soumission
            };

            // Envoyer l'email via EmailJS
            emailjs.send("service_6gjiwu3", "TON_TEMPLATE_ID", templateParams)
                .then(function () {
                    alert("Merci pour votre vote !");
                }, function (error) {
                    alert("Une erreur est survenue lors de l'envoi du vote.");
                    console.error("Erreur :", error);
                });
        }
    </script>
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
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <h1>À la recherche du nouveau nom pour Spine</h1>
    <p>Merci pour vos propositions ! Il est temps de voter pour vos préférées.<br>
        Vous pouvez choisir une ou deux options.</p>
    
    <div class="checkbox-group">
        <p><strong>Les propositions de l'équipe</strong></p>
        <label><input type="checkbox" name="vote" value="Bloom"> Bloom (floraison = croissance)</label><br>
        <label><input type="checkbox" name="vote" value="Content Studio"> Content Studio</label><br>
        <label><input type="checkbox" name="vote" value="Spark"> Spark (l'étincelle qui initie quelque chose de plus grand)</label><br>
        <label><input type="checkbox" name="vote" value="Node"> Node (nœud, intersection, point de connexion entre les contenus, les formats, les plateformes)</label><br>
        <label><input type="checkbox" name="vote" value="Fuse"> Fuse (la fusion/connexion entre les contenus et les plateformes)</label><br>
    </div>

    <button onclick="submitVote()">Soumettre</button>
</body>
</html>
