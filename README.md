<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English to Indonesian Dictionary</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        #search-box {
            margin-bottom: 20px;
        }
        #result {
            display: none;
            margin-top: 20px;
        }
        li {
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <h1>English to Indonesian Dictionary</h1>
    <input type="text" id="search-box" placeholder="Enter English word...">
    <div id="result">
        <h2>Result:</h2>
        <ul id="word-list"></ul>
    </div>

    <script>
        // Dictionary data
        const dictionary = {
            "hello": "halo",
            "goodbye": "selamat tinggal",
            "cat": "kucing",
            // Add more words here
        };

        const searchBox = document.getElementById('search-box');
        const resultDiv = document.getElementById('result');
        const wordList = document.getElementById('word-list');

        searchBox.addEventListener('input', function() {
            const searchTerm = this.value.toLowerCase();
            const result = [];

            if (searchTerm.trim() !== '') {
                for (const word in dictionary) {
                    if (word.includes(searchTerm)) {
                        result.push({ english: word, indonesian: dictionary[word] });
                    }
                }
            }

            displayResult(result);
        });

        function displayResult(result) {
            if (result.length > 0) {
                resultDiv.style.display = 'block';
                wordList.innerHTML = '';

                result.forEach(function(item) {
                    const li = document.createElement('li');
                    li.textContent = `${item.english} - ${item.indonesian}`;
                    wordList.appendChild(li);
                });
            } else {
                resultDiv.style.display = 'none';
            }
        }
    </script>
</body>
</html>
