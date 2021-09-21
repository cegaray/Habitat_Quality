# Estimación de cobertura de la tierra a partir de la herramienta Random Forest. 
Código desarrollado por Carlos A. Morantes
Siga las instrucciones de inicio
Automated RandomForest based on raster and shapefile data
The following code runs an automated Random Forest classifier for pixel value based on the extraction of features from source rasters (variable to be predicted variables) and rasters for the variables you want to use to predict.

It is divided into three main sections. Each section will ask you to provide additional information for the process. Please respond according to the question. Most of them are yes/no questions (you must answer literally and in lower case) or a menu of options. In the latter case, you will be required to write the number corresponding to the option you prefer.

The following is a list of the sections and the required files to run it:

Extracting data : This section loads the necessary libraries for the whole code. It also requires:

A source raster with the projection you will use for all the process.
The set of rasters you will use to create the model. They don't need to have the same projection as the source file (the code will automatically reproject them), but the extension of the source raster MUST BE WITHIN THE EXTENTION OF ALL THE OTHER RASTERS.
A points shapefile (shp) with a field named 'id' that contains an integer identifier for each of the points on the raster you want to use to create the model.
That you choose a name for a text file to store the data for the construction of the model.
The output of this section is a file containing the database of extracted values for the model.
Random Forest : This section constructs the model. It also requires:

A name for the file where the information of the model is stored.
That you select what is your target variable in the model (what you want to predict) and the variables you want to use to predict such a value.
That you choose the number of cores you want to use for running the code (we recommend you to leave at least one core out of the process, sou you can use your computer while the code is running).
That you choose the number of trees for the forest. If you are unsure of the number of trees, use 150, run all the code and then, use the plot of error vs number of trees to assess a proper forest size. Then, run this section again.
The output of this section is the Random Forest model.
Predicting values: This section uses the constructed model to predict future values based on a set of predictive variables. In this case, you MUST have the rasters containing such variables stored within a folder named futurerastes. That folder has to be in the same directory where this code is bein runned. These rasters have to be in the same projection as your shapefile. It also requires:
That ALL the raster you will use to predict have THE EXACT SAME NAME as those you used to create the model in the previous section.
That you choose a name for a text file to store the data for the variables to predict the target values.
That you select how you want to call the target variable in the final database file you will use to rasterize the prediction (it can be any name you want; please avoid starting with numbers, using spaced or hyphens).
The output of this section is a text file with the predicted values for each point of the shapefile corresponding to a position in the raster file). It will also produce:
A plot of importance for each variable.
A plot of error vs number of trees. For this value, you must select a maximum number of trees to test. It must be higher than 16, the minimum number of trees is fixed in 15. This operation can take some time (depending on the maximum number of trees), so grab a cup of coffee after you start running it.
