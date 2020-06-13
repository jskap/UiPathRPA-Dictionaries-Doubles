# UiPathRPA-Dictionaries-Doubles
Calculate the combined weight of the packages sent to one city.

Consider the database of a shipping company containing people and the packages they are sending to certain cities across the world, 
along with their weight. The database is a Dictionary with the key of String type (the names of the persons) and the values of 
Dictionary (String/Cities, Double/Weight) type.

Please calculate the overall weight for one city destination. Once this is done, the user should be presented with an input dialog 
containing the distinct list of cities present in the input data dictionary. If the user chooses no value from the input dialog, 
print "Nothing chosen by the user"; otherwise you can print "The combined weight of the packages sent to <ChosenCity> is x.xx" 
(use double digits).

Note: For input data, download the workflow below, which already has the Dictionary defined.

New Dictionary(Of String, Dictionary(Of String, Double)) From {

{"John C", New Dictionary(Of String, Double) From {{"Madrid",2.1},{"Paris",1.1}}  },

{"Sarah C", New Dictionary(Of String, Double) From {{"New York",2.1},{"Paris",3.3},{"Berlin", 0.8}}  },

{"Kyle R", New Dictionary(Of String, Double) From {{"San Francisco",2.8},{"New York",1.1}}  },

{"Johnny B", New Dictionary(Of String, Double) From {{"New York",2.1},{"Paris",3.3}, {"Cairo",1.3}, {"Chicago",1.9}}  }}


In UiPath Studio, create a new project and use the following steps:

 1. Start the project as a sequence.

 2. Loop through the values of the initial Dictionary using 'For Each' and (in the Body) loop through the keys of the second 
    dictionary (cities) with 'For Each' and check if the city is already in the Dictionary (using 'If' and 'Contains' method):
    
    a. if the condition is met, add the weight stored in the corresponding value to the existing value using an 'Assign' 
       activity;
       
    b. if the condition is not met, add the city in the dictionary with the corresponding value using the 'Invoke Method' 
       activity and 'Add' as MethodName

 3. Use an 'Input Dialog' activity to display all the cities by using SecondVariableName.Keys.ToArray under 'Options' in the 
    activity properties

    a. If the user chooses a city, use 'Write Line' and the 'String.Format' method to print the combined weight.

    b. If the user doesn't choose a city, use 'Write Line' to display a generic message.
