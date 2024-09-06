# Cardio Care Predictor 

- Web Application using Flask REST API which predicts the probability of Coronary Heart Disease in a patient taking 9 different parameters based on the patient's history as input.
- The API uses a Logistic Regression Model from sci-kit-learn trained on the Framingham Heart Study Dataset from Kaggle. The model achieved a test accuracy of around 88%.

## Project Demo
* [Live demo here](https://cardio-care-predictor.netlify.app/)

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Usage](#usage)
* [Contact](#contact)

## General Information About The Project
- We live in an era where computers can predict the weather, stocks, and human thoughts too. Then why are we still lagging back in healthcare, why are we still hearing, “deaths due to sudden cardiac arrest!” 
- Can’t computers predict heart health? No, they can. The only problem is ‘Accessibility’. We need a project wherein a person should be able to check his/her heart health or the probability of having Cardiac disease ANYTIME, ANYWHERE, EASILY, FOR FREE. Just with some common inputs!!
- Once the diagnosis is done, the project should suggest measures accordingly.
- We have developed a web application that can easily predict the possibility of a user having a heart attack.
- With the help of HTML form we will collect the data from the user, and integrate it with javascript, and with the help of health API, we will showcase the percentage of risk of having cardiac arrest, also suggesting tips accordingly.
- The project also consists of a chatbot that will be used for Hospital appointment booking when the user gets acknowledged as high-risk.
- The second major element of the website is the Advanced BMI/BMR calculator.
The calculator will subsequently also show how little or more the weight of the user is, the calories required to get in balance, tips according to the BMI, BMR charts, etc.
The final part of the project displays the various heart diseases linked directly or indirectly, showing their symptoms, precautions, and the best hospital in India for a particular disease, locating it with the help of Google Maps API on our website.
- Website will be responsive so as to be accessible on mobile phones, tablets, laptops, and PCs. To make the website function quickly, the website is authentication-free, and there is no database attached and no data has been stored that will also maintain the privacy of the user's medical details. 

## Usage
- It's Easy to Use Website
- Input generic information like age, sex, no. of cigarettes smoked per day, cholesterol level, blood pressure, whether diabetic patient, sugar level, and heart rate.
- For BMI, BMR input height, weight, age, and exercise type.

## Technologies Used
- HTML5
- CSS3
- Javascript
- [Flask REST API](https://cardio-care-predictor-api.onrender.com/)

```
setTimeout(() => {
        fetch(`https://cardio-care-predictor-api.onrender.com/predict?age=${age}&sex=${sex}&cigs=${cigs}&chol=${cholestrol}&sBP=${sBP}&dia=${diabetes}&dBP=${dBP}&gluc=${glucose}&hRate=${heartRate}`)
        .then(res => res.json())
        .then(data => {
          prediction = parseFloat(data['probability'][0][1]).toFixed(5);
          console.log(prediction)
          document.querySelector('.loader').style.display = 'none';
          if (cigs > 0 & prediction > 0.07) {
            document.querySelector('.clearfix').innerHTML = `
            <p class="nl-form">Quit Smoking Today<br>Predicted probability of having coronary heart disease (Heart Attack)is ${prediction*100} % <br>Please Consult Cardiologist</p>`;
          }
          else if (cigs > 1 & prediction < 0.07){
            document.querySelector('.clearfix').innerHTML = `
            <p class="nl-form">Quit Smoking Today<br>Predicted probability of having a coronary heart disease (Heart Attack) is ${prediction*100} %</p>`;
          }
            else{
              document.querySelector('.clearfix').innerHTML = `
              <p class="nl-form">Predicted probability of having a coronary heart disease (Heart Attack) is ${prediction*100} %</p>`;} 
        })
   ```
