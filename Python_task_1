import pandas as pd
#solution 1
def generate_car_matrix(dataset_path):
        df = pd.read_csv(dataset.1)
       car_df = df.pivot(index='id_1', columns='id_2', values='car')

       car_df = car_df.fillna(0)
      car_df.values[[range(car_df.shape[0])]*2] = 0

      return car_df


dataset_path = 'dataset1.csv'
result = generate_car_matrix(dataset1.csv)
print(result)
*******************************************************************************************************
#solution 2

def get_type_count(df):
   
    low_condition = df['car'] <= 15
    medium_condition = (df['car'] > 15) & (df['car'] <= 25)
    high_condition = df['car'] > 25

   
    df.loc[low_condition, 'car_type'] = 'low'
    df.loc[medium_condition, 'car_type'] = 'medium'
    df.loc[high_condition, 'car_type'] = 'high'


    type_counts = df['car_type'].value_counts().to_dict()

   
    sorted_type_counts = dict(sorted(type_counts.items()))

    return sorted_type_counts

df = pd.read_csv('dataset-1.csv')  
result_type_counts = get_type_count(df)
print(result_type_counts)
******************************************************************************************************
#solution 3
def get_bus_indexes(df):
    
    bus_indexes = df[df['bus'] > 2 * mean_bus].index.tolist()
    sorted_bus_indexes = sorted(bus_indexes)

    return sorted_bus_indexes


df = pd.read_csv('dataset-1.csv') 
result_bus_indexes = get_bus_indexes(df)
print(result_bus_indexes)

***********************************************************************************************************
#solution 4
def filter_routes(df):
   
    route_avg_truck = df.groupby('route')['truck'].mean()

  
    filtered_routes = route_avg_truck[route_avg_truck > 7].index.tolist()

    
    sorted_filtered_routes = sorted(filtered_routes)

    return sorted_filtered_routes


df = pd.read_csv('dataset-1.csv')  
result_filtered_routes = filter_routes(df)
print(result_filtered_routes)
*************************************************************************************************************
#Solution 5
def multiply_matrix(matrix):
    

    data1 = matrix.applymap(lambda x: x * 0.75 if x > 20 else x * 1.25)

   
    rounded_matrix = data1.round(1)

    return rounded_matrix


matrix_df = pd.read_csv(df)  
result_modified_matrix = multiply_matrix(matrix_df)
print(result_modified_matrix)
*****************************************************************************************************************
#solution 6
def time_check(df):
    
  
    df['timestamp'] = pd.to_datetime(df['startDay'] + ' ' + df['startTime']) + pd.to_timedelta(df['endTime'])

    completeness_check = df.groupby(['id', 'id_2']).apply(check_timestamp_completeness)

    return completeness_check

def check_timestamp_completeness(group):
   

   
    full_day_coverage = group['timestamp'].min().hour == 0 and group['timestamp'].max().hour == 23

   
    days_coverage = set(group['timestamp'].dt.dayofweek) == set(range(7))

    return full_day_coverage and days_coverage


df = pd.read_csv('dataset-2.csv')  
result_series = time_check(df)
print(result_series)
