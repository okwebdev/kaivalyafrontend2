navbar:

mounted fetches data from api address

makes projects into the data (as a proxy?) after checking for errors

computed - function 'filtered projects' maps the data into an object and checks if it has specific attributes with ? 
which it then maps to the corresponding name, then returns the objects in array filtered by the current 
'active category' which is set by an @click on the menu bar buttons

so filtered objects only contains the objects that correspond to the active category number

navbar is conditionally rendered based on inverse of splashstatus, video disapeers when spalshstatus is false
