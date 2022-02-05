## <b>Mortage prepayment prediction Application</b>

This application is a simple mortage prepayment application which uses a ML trained model to predict weather a person prepays the mortage earlier their allocated time. By using such prediction model banks prevent the risk that can occure.

### <u> Description of the web application </u>
The web application uses simple techniques for it's implementaion.

* <b> HTML & CSS</b> for the fromend part.
* <b> Django </b> is used in backend.


### Workflow of the project

The user inputs necessary data into the form like structure and once click the predict button the result is displayed on the screen itself. 

Logic behind:

The main file that we need o focus on is views.py. 

STEP 1:  
We have done necessary imports of the library that we need to implement our logic.

```python
from django.shortcuts import render
from django.http import HttpResponse
import pandas as pd
import numpy as np
import gzip,pickle
from sklearn.preprocessing import StandardScaler
import joblib
```


STEP 2:  
After that we read the pickled file using the Joblib library.

STEP 3:

Then we define a function named predict prepayment where we basically take in the input from the user and then convert the input into the float format and then scale down the value and finally call the <b>.predict</b>  function which does the prediction job.


```python
# Demo

if request.method == 'POST':

        temp={}
        temp['flag_yes']=float(request.POST.get('flag_yesVal'))
        temp['flag_no']=float(request.POST.get('flag_noVal'))
```

```python

testData=pd.DataFrame({'x':temp}).transpose()
        
        final_features_scaled = standard_to.fit_transform(testData)
        prediction = new_model.predict(final_features_scaled)


        if(int(prediction) == True):

            result = "It is a prepaid condition"

        else:
            result = "It is Non-prepaid condition"


        

    return render(request,'index.html',{'result' : result})


```
### <b> Screenshots of the result:</b>







### <b> IMPORTANT</b>

We need to make proper configuration of the methods that we use in the views.py in our <b>urls.py</b> of our main folder. In our case <b>ModelDeployment folder</b>.

```python
# In urls.py

from django.contrib import admin
from django.urls import path
from django.conf.urls import url
from Firstpage import views

urlpatterns = [
    path('admin/', admin.site.urls),
    url('^$',views.index,name = 'Homepage'),
    url('predictPrepayment',views.predictPrepayment,name ='predictPrepayment'),
]

```

Also don't forget to configure templates folder in <b>settings.py</b> of the main folder.


```python
# In settings.py

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR,'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

```

### Screenshot of the project

#### UI of the project

![image](https://user-images.githubusercontent.com/57294017/152632487-700ded30-d8a4-4fbb-970a-621e81188562.png)


![image](https://user-images.githubusercontent.com/57294017/152632519-f5a1abcb-148a-4d1b-b7d9-dce301012c51.png)

![image](https://user-images.githubusercontent.com/57294017/152632529-c4696a71-0b27-4188-97f0-6fb675cce0d5.png)


### Result for the prediction

![image](https://user-images.githubusercontent.com/57294017/152632650-bc9f5520-23d1-4b6a-8912-0e2d7c930562.png)




