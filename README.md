# dbss
from flask import Flask, render_template, request
import joblib

app = Flask(__name__)

@app.route("/",methods=["GET","POST"])
def index():
    return(render_template("index.html"))

@app.route("/prediction",methods=["GET","POST"])
def prediction():
    q = float(request.form.get("q"))
    return(render_template("prediction.html",r=(-50.6*q)+90.2))

if __name__ == "__main__":
    app.run()
index.html
<head>
    <meta name="viewport"
        content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="{{ url_for('static',
        filename='styles.css') }}">
</head>
<body>
    <div class="container">
    <h2>DBS share price prediction</h2>
        <form action="/prediction" method="post">
            <p>Please enter USD/SGD exchange rate </p>
            <input type="number" step="0.01" name="q">
            <input type="submit" value="Enter">
        </form>
    </div>
</body>
