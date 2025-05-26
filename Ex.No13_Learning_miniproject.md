# Ex.No: 13 Learning – Use Supervised Learning  
### DATE:                                                                            
### REGISTER NUMBER : 212222043008
### AIM: 
To write a program to train the classifier for -----------------.
###  Algorithm:
Step 1: Import packages Step 2: Get the data Step 3: Split the data Step 4: Scale the data Step 5: Instantiate model Step 6: Create a function for gradio Step 7: Print Result
### Program:
```
import numpy as np
import pandas as pd
pip install gradio
pip install typing-extensions --upgrade
pip install --upgrade typing
pip install typing-extensions --upgrade
import gradio as gr
data = pd.read_csv('/content/diabetes.csv')
data.head()
print(data.columns)
x = data.drop(['Outcome'], axis=1)
y = data['Outcome']
print(x[:5])
#split data
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test= train_test_split(x,y)

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.fit_transform(x_test)

from sklearn.neural_network import MLPClassifier
model = MLPClassifier(max_iter=1000, alpha=1)
model.fit(x_train, y_train)
print("Model Accuracy on training set:", model.score(x_train, y_train))
print("Model Accuracy on Test Set:", model.score(x_test, y_test))

def diabetes(Pregnancies, Glucose, Blood_Pressure, SkinThickness, Insulin, BMI,Diabetes_Pedigree, Age):
    x = np.array([Pregnancies,Glucose,Blood_Pressure,SkinThickness,Insulin,BMI,Diabetes_Pedigree,Age])
    prediction = model.predict(x.reshape(1, -1))
    if(prediction==0):
      return "NO"
    else:
      return "YES"

outputs = gr.Textbox()
app = gr.Interface(fn=diabetes, inputs=['number','number','number','number','number','number','number','number'], outputs=outputs,description="Detection of Diabeties")
app.launch(share=True)
```
### Output:
1.Dataset

![327995224-05887a4c-0fb7-4e5d-8d7a-b5fa800143f7](https://github.com/user-attachments/assets/104a8fbc-279c-41aa-95c1-aa1549ea76ea)

2.Accuracy

![327995294-431761f2-3b1c-4b9c-81aa-1ec8ad6a3ab6](https://github.com/user-attachments/assets/7a1eae35-e978-478c-976c-b05a23d253b4)

3.Output

![327995474-d2eff3be-b1dd-44eb-93b9-b6f397130a5e](https://github.com/user-attachments/assets/960eb83d-05c6-4d67-9922-36803fcdccd9)

### Result:
Thus the system was trained successfully and the prediction was carried out.
