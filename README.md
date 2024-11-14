# combine-multiple-excel-in-to-one-files
This python script will be helping you combining multiple excel files into one files for data analysis purpose

#Tips for Large Files

#Load Only Necessary Columns: Use usecols in pd.read_excel() to load only specific columns if not all columns are required.

df = pd.read_excel(file, usecols=['Column1', 'Column2'], engine='openpyxl')

#Adjust Data Types: Convert data types (e.g., integers to smaller integer types) if possible to reduce memory usage.

#Write to CSV if Excel File Size Exceeds Limits: 

#Excel has a size limit of ~1 million rows. For very large data, consider saving to CSV:

combined_df.to_csv('combined_output.csv', index=False)

#This script will handle combining large files efficiently while keeping memory usage manageable. Let me know if you have specific requirements for filtering or processing data within each file!

#Chunk Processing (if needed): If your system has memory constraints, you can process the Excel file in chunks. This is helpful for very large files.

chunk_size = 50000  # Adjust chunk size based on your memory capacity
for chunk in pd.read_excel(excel_file, chunksize=chunk_size, engine='openpyxl'):
    chunk.to_csv(csv_file, mode='a', index=False, header=not pd.io.common.file_exists(csv_file))
    
#Compression (Optional): To further reduce the file size, you can compress the CSV using gzip:

df.to_csv(csv_file, index=False, compression='gzip')
