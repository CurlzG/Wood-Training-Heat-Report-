# Wood-Training-Heat-Report-
For the last three months, I worked as an interim reasearcher and was tasked with researching about what heat stress and how it affects the body, then identify what device would achieve this the best and then test the device on the firefighter during the testing phase and record the information and come to the conclusion about if the firefighters were suffering from heat stress. </br> 
</br>
Below is the article and the report showing the outcome of everything </br>

## Link To Article
This is the link, to the article post about report <br/>
https://www.woodtraining.co.nz/heat-stress-monitoring/?fbclid=IwAR2WUJ2YVd1VCg2Jgg1q6uKsIkLgjbpXfhhrHbnGu2GRsBsV8u0STGf8aI8


## Link To Report
https://www.woodtraining.co.nz/wp-content/uploads/2022/04/Wearable-Sensors-Project-PUBLIC.pdf


## Testing Part
For the testing part, I developed an air temperature sensor that would display the temperature on screen.  </br>
For recording the information I developed an react native application, that could easily record information quickly and allow me to share in a csv format for to be allow to align with the data from the device. </br>


### Python Script
Due to an erorr, I would create uncessary data entries and due to the amount I was writing during the day, I didnt really didnt even have a chance to be able to delete it, so I created a script, to just return the note and time it was created. 

````
# Getting the Notes and Returning the String
def cleanState(file):
    actions = {}
    for x in file:
        x = x.replace("\n", "")
        cleantext = ""
        fulltext = ""
        count = 0
        # Searching for "Date," then returning the string before Date
        while count != len(x):
            fulltext = fulltext + x[count]
            if x[count] == ",":
                if count + 5 < len(x):
                    if x[count + 1] == "D":
                        if x[count + 2] == "a":
                            if x[count + 3] == "t":
                                if x[count + 4] == "e":
                                    if x[count + 5] == ",":
                                        count == len(x)
                                        break
            else:
                cleantext = cleantext + x[count]
            count = count + 1
        # Example Changes 11:45:0 to 11:45:00
        time = x[((len(x) - 1) - 7):len(x) - 1] + "0"
        # Example Changes ,9:43:00 to 09:43:00
        if "," in time:
            time = time.replace(",", "0")
        actions[time] = cleantext

    print("Length of Actions -->", len(actions))  # Checking if the Actions Size matches the list of notes size
    return actions
````
An example of this would be </br>
Original Note </br>
Both outside rftb ,Date,1/3/2022,Time,11:45:0, </br>
New Note Output </br>
11:45:00, Both outside rftb </br>
