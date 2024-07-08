# Car-Valuation

### Approach Followed in the ML Model Training Code

1. **Imports and Settings**
   - **Libraries**: The code imports necessary libraries for data manipulation (`pandas`, `numpy`), model building (`sklearn`), and warnings management.
   - **Settings**: It sets display options for `pandas` to show all columns and suppresses warnings.

2. **Data Augmentation**
   - **Function Definition**: A function `augment_data` is defined to augment the dataset by creating new samples. This involves:
     - Creating derived features such as current year and month.
     - Converting month names to numerical values.
     - Randomly altering numerical features slightly to create new samples.

3. **Data Preprocessing**
   - **Imputation**: Missing values are handled using `SimpleImputer`.
   - **Encoding**: Categorical variables are encoded using `OneHotEncoder`.
   - **Scaling**: Numerical features are scaled using `StandardScaler`.
   - **Column Transformation**: `ColumnTransformer` is used to apply different preprocessing steps to different columns in the dataset.

4. **Model Building**
   - **Pipeline Creation**: A `Pipeline` is created to streamline the preprocessing and model training steps.
   - **Model Selection**: A `RandomForestRegressor` is chosen as the model for regression tasks.
   - **Hyperparameter Tuning**: `GridSearchCV` is used for hyperparameter tuning to find the best model parameters.

5. **Model Evaluation**
   - **Metrics**: The model is evaluated using metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared score.

6. **Warnings and Display Settings**
   - Warnings are filtered out to ensure a cleaner output during the model training process.
   - `pandas` settings are adjusted to display all columns in the dataset.

### New Features Added to the Base Dataset

1. **Derived Features**
   - **Current Year and Month**: These are derived from the current date and used to create or modify features.
     - `current_year`: Current year.
     - `current_month`: Current month.

2. **Month Conversion**
   - **Month Names to Numbers**: Month names in the feature `month_of_vehicle_manufacture` are converted to numerical values.
     - The `month_to_number` dictionary maps month names to their respective numerical values.
     - This ensures that month names are standardized to numeric values.

3. **Random Alterations to Existing Features**
   - **Odometer Reading**: The `odometer_reading` feature is randomly altered slightly by multiplying with a random factor between 0.9 and 1.1.
     - This introduces slight variations in the odometer readings of the augmented samples.
   
   - **Month of Vehicle Manufacture**: The `month_of_vehicle_manufacture` feature is altered by adding or subtracting 1 randomly, ensuring the value remains between 1 and 12.
     - This introduces slight variations in the month of manufacture of the vehicle.

   - **Year of Vehicle Manufacture**: The `year_of_vehicle_manufacture` feature is altered by adding or subtracting 1 randomly, ensuring the value remains within the range from 1980 to the current year.
     - This introduces slight variations in the year of manufacture of the vehicle.

   - **Car Valuation**: The `car_valuation` feature is slightly altered by multiplying with a random factor between 0.95 and 1.05.
     - This introduces slight variations in the car valuation of the augmented samples.

4. **Creation of New Features**
   - **Luxury Feature**: A new feature `is_luxury` is created based on the vehicle's make, variant, and model. Vehicles from luxury makes like Mercedes-Benz, BMW, Audi, etc., or variants and models like S-Class, 7-Series, etc., are marked as luxury.
   - **Commercial Vehicle Feature**: A new feature `is_commercial` is created based on the vehicle's make and model. Vehicles from commercial makes like Tata, Mahindra, etc., or models like Eeco, Bolero, etc., are marked as commercial.
   - **Scrappage Risk**: A feature `scrappage_risk` is created based on the vehicle's age and other factors to estimate the risk of the vehicle being scrapped.
   - **City Category**: A feature `city_category` is created to categorize cities into different tiers based on their characteristics.

These derived and altered features help in creating a more diverse and robust dataset for training the machine learning model, thereby improving its performance and generalizability.
