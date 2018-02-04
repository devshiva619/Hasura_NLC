# Watson-Natural Language Classifier

This is a simple application that enables text classification using IBM Watson's Natural Language Understanding.

**Features** 
    
* Recieves text from the user through a minimalist interface.
* Provides three possible classifications for the inputted text.
* Provides a confidence value for each of the classifications.

The application builds on top of the [Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/?python#post-analyze) API developed by IBM.

### Codebase Structure
All of the backend code is in one file that you can read at: `/Python-Flask/microservices/watson/src/server.py` 

All of the frontend code is in one file that you can read at: `/React_Native/App.js `

### Backened API Use Guide
* Send a POST request payload to Flask backend at `/`
* Request Format:
    ```
    {
      method: "POST",
      headers: {
       "Accept": "application/json",
       "Content-Type": "multipart/form-data"
      },
      body: <payload>
   }    
   ```
   
* The Payload must contain a key value pair "text":"Text to be analyzed here"
* The backend returns the computed result in the form of JSON. Example JSON:
    ```JSON
    {
        " categories ": [
            {
            " label ": "/ technology and computing
            / software / databases " ,
            " score ": 0.436991
            },
            {
            " label ": "/ technology and computing
            / programming languages / java " ,
            " score ": 0.311278
            },
            {
            " label ": "/ health and fitness / disease
            / headaches and migraines " ,
            " score ": 0.259054
            }
        ],
        " language ": " en " ,
        " usage ": {
            " features ": 1 ,
            " text_characters ": 300 ,
            " text_units ": 1
        }
    }
    ```

### Frontend Application 
* Simply download and install the application found at `/React_Native/app-release.apk `
* Input the text to be classified into the given textbox. 
![Text](https://raw.githubusercontent.com/HPDF-64/Hasura_NLC/master/Readme_Files/before.png)

* Tap Analyze to receive your results.
![Text](https://raw.githubusercontent.com/HPDF-64/Hasura_NLC/master/Readme_Files/after.png)

### For Deployment
* In `/Python-Flask/microservices/watson/src/server.py` replace the username and password with your IBM BlueMix credentials.
* Push these changes to your Hasura cluster using Hasura's CLI.
    ```
    $ git add .
    $ git commit -m "<Commit Message>"
    $ git push hasura master
    ```