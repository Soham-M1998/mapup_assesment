import pandas as pd
****************************************************************************************************************************
#solution 1
import numpy as np

def calculate_distance_matrix(df):
    
    distances_df = df.pivot(index='from_toll', columns='to_toll', values='distance').fillna(0)

   
    distances_array = distances_df.to_numpy()

    
    distances_array = distances_array + distances_array.T - np.diag(distances_array.diagonal())

  
    cumulative_distances_df = pd.DataFrame(np.tril(distances_array), index=distances_df.index, 
    columns=distances_df.columns)

    return cumulative_distances_df

df = pd.read_csv('dataset-2.csv')  
result_matrix = calculate_distance_matrix(df)
print(result_matrix)
****************************************************************************************************************************
#solution 2

def unroll_distance_matrix(df):
    
    stacked_series = df.stack()
    
    
    unrolled_df = stacked_series.reset_index()
    
  
    unrolled_df.columns = ['id_start', 'id_end', 'distance']
    
   
    unrolled_df = unrolled_df[unrolled_df['id_start'] != unrolled_df['id_end']].reset_index(drop=True)
    
    return unrolled_df


unrolled_df = unroll_distance_matrix(df)
print(unrolled_df)
*******************************************************************************************************************************
#solution 3
def find_ids_within_ten_percentage_threshold(df, reference_id):
    
    reference_rows = df[df['id_start'] == reference_id]
    
    
    reference_avg_distance = reference_rows['distance'].mean()
    
    
    lower_bound = reference_avg_distance - 0.1 * reference_avg_distance
    upper_bound = reference_avg_distance + 0.1 * reference_avg_distance
    
    
    result_df = df.groupby('id_start')['distance'].mean().reset_index()
    result_df = result_df[(result_df['distance'] >= lower_bound) & (result_df['distance'] <= upper_bound)]
    
   
    result_df = result_df.sort_values(by='distance').reset_index(drop=True)
    
    return result_df


result_within_threshold = find_ids_within_ten_percentage_threshold(unrolled_df, reference_id=your_reference_id)
print(result_within_threshold)
**********************************************************************************************************************************
solution 4
def calculate_toll_rate(df):
    
    rate_coefficients = {'moto': 0.8, 'car': 1.2, 'rv': 1.5, 'bus': 2.2, 'truck': 3.6}
    
    
    for vehicle_type, rate_coefficient in rate_coefficients.items():
        df[vehicle_type] = df['distance'] * rate_coefficient
    
    return df


result_with_toll_rate = calculate_toll_rate(unrolled_df)
print(result_with_toll_rate)
************************************************************************************************************************************
solution 5
def calculate_time_based_toll_rates(df)->pd.DataFrame():
    """
    Calculate time-based toll rates for different time intervals within a day.

    Args:
        df (pandas.DataFrame)

    Returns:
        pandas.DataFrame
    """
    # Write your logic here

    return df
