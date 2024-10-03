# AIML-Lab

# Import required libraries
import pandas as pd

# Function to load a dataset
def load_data(file_path):
    """
    Load the dataset from the specified CSV file.

    Parameters:
    file_path (str): The path to the CSV file to be loaded.

    Returns:
    pandas.DataFrame: Loaded DataFrame.
    """
    try:
        data = pd.read_csv(file_path)
        print("Data successfully loaded!")
        return data
    except FileNotFoundError:
        print("File not found. Please check the file path.")
        return None

# Function to display dataset details
def show_dataset_info(data):
    """
    Display basic details of the dataset such as number of rows and columns, 
    first five rows, size, number of missing values, and summary statistics for numerical columns.

    Parameters:
    data (pandas.DataFrame): The dataset to analyze.
    """
    if data is None:
        print("No data to display. Please load the data first.")
        return
    
    print("\nDataset Information:")
    print("-" * 30)
    
    # Number of rows and columns
    rows, columns = data.shape
    print(f"Number of Rows: {rows}")
    print(f"Number of Columns: {columns}")
    
    # First five rows
    print("\nFirst five rows of the dataset:")
    print(data.head())
    
    # Size of the dataset (total elements)
    print(f"\nSize of dataset (number of elements): {data.size}")
    
    # Check for missing values
    print(f"\nNumber of missing values in each column:\n{data.isnull().sum()}")
    
    # Summary statistics of numerical columns
    print("\nSummary statistics for numerical columns:")
    print(data.describe())
    
    # Sum, average, minimum, and maximum of numerical columns
    print("\nSum of numerical columns:")
    print(data.sum(numeric_only=True))
    
    print("\nAverage of numerical columns:")
    print(data.mean(numeric_only=True))
    
    print("\nMinimum values of numerical columns:")
    print(data.min(numeric_only=True))
    
    print("\nMaximum values of numerical columns:")
    print(data.max(numeric_only=True))

# Function to export the modified dataset to a new CSV file
def export_data(data, output_file_path):
    """
    Export the dataset to a CSV file.

    Parameters:
    data (pandas.DataFrame): The dataset to be exported.
    output_file_path (str): The path to the output CSV file.
    """
    if data is None:
        print("No data to export. Please load the data first.")
        return
    
    try:
        data.to_csv(output_file_path, index=False)
        print(f"Data successfully exported to {output_file_path}")
    except Exception as e:
        print(f"An error occurred while exporting data: {e}")

# Main function to orchestrate the program
def main():
    # File paths
    input_file_path = 'input_data.csv'  # Replace with the path to your input file
    output_file_path = 'output_data.csv'  # Replace with the path to your output file
    
    # Step 1: Load the dataset
    data = load_data(input_file_path)
    
    # Step 2: Show dataset details
    show_dataset_info(data)
    
    # Step 3: Export the dataset to a new CSV file
    export_data(data, output_file_path)

# Execute the program
if _name_ == "_main_":
    main()
