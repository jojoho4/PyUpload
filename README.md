from flask import Flask, request, render_template

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def upload_file():
    if request.method == 'POST':
        uploaded_file = request.files['file']
        if uploaded_file.filename != '':
            # Speichere das hochgeladene Python-Programm
            uploaded_file.save(uploaded_file.filename)
            return 'Datei erfolgreich hochgeladen!'
    return render_template('upload.html')

if __name__ == '__main__':
    app.run(debug=True)

