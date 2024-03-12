<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reliabilty</title>
    <!-- <link rel="stylesheet" href="style.css"> -->
    <style>
        div {
            font-family: Arial, sans-serif;
            text-align: center;
            font-size: 2rem;
            font-weight: bold;
        }

        h1 {
            font-family: Arial, Helvetica, sans-serif;
        }

        body {
            font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        }

        button {
            margin-top: 15px;
            margin-bottom: 15px;
            background-color: hsl(212, 12%, 28%);
            color: white;
            font-size: 1.5em;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: hsl(212, 12%, 38%);
        }

        button:active {
            background-color: hsl(212, 12%, 48%);
        }

        input {
            width: fit-content;
            text-align: center;
            font-size: 1.5em;
            border: 2px solid hsla(0, 0%, 0%, 0.8);
            border-radius: 5px;
            margin-bottom: 15px;
        }

        label {
            font-size: 1.5em;
            font-weight: bold;
        }
    </style>
</head>

<body>
    <div id="container">
        <h1>Jerum's BPO Reliabilty Scorer</h1>
        <label>Days Present:</label>
        <input type="number" id="daysPresent" value="23" min="1" max="23"><br>
        <label>Hours late:</label>
        <input type="number" id="hoursLate" value="0" min="0" max="8"><br>
        <label>Minutes late:</label>
        <input type="number" id="minutesLate" value="0" min="0" max="60"><br>
        <button onclick="getReliabilty()">Calculate Reliabilty</button><br>
        <label> Result percentage:</label>
        <input type="number" id="showResult">
    </div>
    <script>
        getReliabilty = () => {
            const daysPresent = document.getElementById("daysPresent").value;
            const hoursLate = Number(document.getElementById("hoursLate").value);
            const minutesLate = Number(document.getElementById("minutesLate").value);
            const relResult = document.getElementById("showResult");
            const hoursPerDay = 8.0;
            const daysPerMonth = 23.0;
            const perfectScore = hoursPerDay * daysPerMonth;
            let reliabiltyScore = ((daysPresent * hoursPerDay) - (hoursLate + (minutesLate / 60)))
                / perfectScore * 100;
            relResult.value = reliabiltyScore.toFixed(2);
        }
    </script>
</body>

</html>