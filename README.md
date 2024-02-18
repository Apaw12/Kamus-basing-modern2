<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English-Indonesian Dictionary</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        h1 {
            text-align: center;
        }
        #search-box {
            margin: 20px auto;
            display: block;
            padding: 10px;
            width: 300px;
            font-size: 16px;
        }
        #result {
            margin: 20px auto;
            max-width: 500px;
        }
        li {
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <h1>English-Indonesian Dictionary</h1>
    <input type="text" id="search-box" placeholder="Enter word...">
    <div id="result">
        <h2>Result:</h2>
        <ul id="word-list"></ul>
    </div>

    <script>
        const dictionary = {
            "hello": "halo",
            "goodbye": "selamat tinggal",
            "cat": "kucing",
            "dog": "anjing",
            // Add more words here
        };

        const searchBox = document.getElementById('search-box');
        const wordList = document.getElementById('word-list');

        searchBox.addEventListener('input', function() {
            const searchTerm = this.value.trim().toLowerCase();
            const result = [];

            if (searchTerm !== '') {
                for (const [englishWord, indonesianWord] of Object.entries(dictionary)) {
                    if (englishWord.includes(searchTerm) || indonesianWord.includes(searchTerm)) {
                        result.push({ english: englishWord, indonesian: indonesianWord });
                    }
                }
            }

            displayResult(result);
        });

        function displayResult(result) {
            const wordList = document.getElementById('word-list');
            wordList.innerHTML = '';

            if (result.length > 0) {
                result.forEach(function(item) {
                    const li = document.createElement('li');
                    li.textContent = `${item.english} - ${item.indonesian}`;
                    wordList.appendChild(li);
                });
            } else {
                const li = document.createElement('li');
                li.textContent = 'No matching words found.';
                wordList.appendChild(li);
            }
        }
    </script>
</body>
</html>
