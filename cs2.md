# Dictionary to DataFrame

>In this example I displayed the methods behind dictionaries and how you can transfer one to a pandas DataFrame. In the pandas DataFrame I was able to organize the data by datetime which is often a useful data organizational tactic. Dictionaries are composed of key-value pairs, where the keys correspond to a list of values.


```python
#Import pandas package
import pandas as pd
```

Make a list for each pandas DataFrame column, keeping all indexes corresponding to the same data consistent/in order across each list:



```python
course_data = {"Due_Date": ['2020-10-2', '2020-10-7', '2020-12-6', '2020-11-9', 
                            '2020-9-26', '2020-12-1'],
               'Time': [23.59,12.00,23.59,23.59,7.00,10.00], 
               'Class_Name': ['a', 'b', 'c', 'd', 'e', 'c'], 
               'Course_Code': ['NESC 1', 'NESC 2', 'NESC 3', 'NESC 4', 'NESC 5', 
                               'NESC 3'], 
               'Assignment_Type': ['Reading', 'Exam', 'Discussion' 'post', 'Demo',
                                   'Test', 'Project' ], 
               'To_Do': ['Ch.1, Ch. 2', 'Ch. 7, Ch.9(p.333-335)', 'Lecture 1 & 2', 
                         'Find relevant topic', 'Ch.1 & Ch.2-2.5', 
                         'course material application'], 
               'Complete?': ['yes', 'no', 'no', 'no', 'yes', 'no'],
               'Grade': [float('NaN'), 0, 0, 0, 45/48, 0]}
```

Applying the .keys() method to the dictionary outputs a list of all the keys present in the dictionary:


```python
course_data.keys()
```




    dict_keys(['Due_Date', 'Time', 'Class_Name', 'Course_Code', 'Assignment_Type', 'To_Do', 'Complete?', 'Grade'])



To access all the elements within a key, call a key within square brackets on the dictionary:


```python
course_data['Course_Code']
```




    ['NESC 1', 'NESC 2', 'NESC 3', 'NESC 4', 'NESC 5', 'NESC 3']



Inserting the column labels into a pandas DataFrame which conveniently fills in the DataFrame values with the each list of elements corresponding to the keys:


```python
course_data_df = pd.DataFrame(course_data, columns = ['Due_Date', 'Time', 'Class_Name',
                                                      'Course_Code', 'Assignment_Type', 
                                                      'To_Do', 'Complete?', 'Grade'])

print(course_data_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    0  2020-10-2  23.59          a      NESC 1         Reading   
    1  2020-10-7  12.00          b      NESC 2            Exam   
    2  2020-12-6  23.59          c      NESC 3  Discussionpost   
    3  2020-11-9  23.59          d      NESC 4            Demo   
    4  2020-9-26   7.00          e      NESC 5            Test   
    5  2020-12-1  10.00          c      NESC 3         Project   
    
                             To_Do Complete?   Grade  
    0                  Ch.1, Ch. 2       yes     NaN  
    1       Ch. 7, Ch.9(p.333-335)        no  0.0000  
    2                Lecture 1 & 2        no  0.0000  
    3          Find relevant topic        no  0.0000  
    4              Ch.1 & Ch.2-2.5       yes  0.9375  
    5  course material application        no  0.0000  


Converting the date column ('Due_Date') to datetime allows the data to be sorted by date:


```python
course_data_df["Due_Date"]=pd.to_datetime(course_data_df["Due_Date"])
sorted_df = course_data_df.sort_values(by="Due_Date")
print(sorted_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    4 2020-09-26   7.00          e      NESC 5            Test   
    0 2020-10-02  23.59          a      NESC 1         Reading   
    1 2020-10-07  12.00          b      NESC 2            Exam   
    3 2020-11-09  23.59          d      NESC 4            Demo   
    5 2020-12-01  10.00          c      NESC 3         Project   
    2 2020-12-06  23.59          c      NESC 3  Discussionpost   
    
                             To_Do Complete?   Grade  
    4              Ch.1 & Ch.2-2.5       yes  0.9375  
    0                  Ch.1, Ch. 2       yes     NaN  
    1       Ch. 7, Ch.9(p.333-335)        no  0.0000  
    3          Find relevant topic        no  0.0000  
    5  course material application        no  0.0000  
    2                Lecture 1 & 2        no  0.0000  


To convert the 'Grade' column values into percent, multiply the column by 100:


```python
sorted_df['Grade']=sorted_df['Grade']*100
print(sorted_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    4 2020-09-26   7.00          e      NESC 5            Test   
    0 2020-10-02  23.59          a      NESC 1         Reading   
    1 2020-10-07  12.00          b      NESC 2            Exam   
    3 2020-11-09  23.59          d      NESC 4            Demo   
    5 2020-12-01  10.00          c      NESC 3         Project   
    2 2020-12-06  23.59          c      NESC 3  Discussionpost   
    
                             To_Do Complete?  Grade  
    4              Ch.1 & Ch.2-2.5       yes  93.75  
    0                  Ch.1, Ch. 2       yes    NaN  
    1       Ch. 7, Ch.9(p.333-335)        no   0.00  
    3          Find relevant topic        no   0.00  
    5  course material application        no   0.00  
    2                Lecture 1 & 2        no   0.00  


As you complete assignments, you can use the loc function and the row index and column to locate the value and change it to 'yes' to signify that it has been completed:


```python
sorted_df.loc[5,'Complete?'] = 'yes'
print(sorted_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    4 2020-09-26   7.00          e      NESC 5            Test   
    0 2020-10-02  23.59          a      NESC 1         Reading   
    1 2020-10-07  12.00          b      NESC 2            Exam   
    3 2020-11-09  23.59          d      NESC 4            Demo   
    5 2020-12-01  10.00          c      NESC 3         Project   
    2 2020-12-06  23.59          c      NESC 3  Discussionpost   
    
                             To_Do Complete?  Grade  
    4              Ch.1 & Ch.2-2.5       yes  93.75  
    0                  Ch.1, Ch. 2       yes    NaN  
    1       Ch. 7, Ch.9(p.333-335)        no   0.00  
    3          Find relevant topic        no   0.00  
    5  course material application       yes   0.00  
    2                Lecture 1 & 2        no   0.00  


## Trial Errors

When trying to create a value under the column 'Grade', I tried to assign one of the rows 'NaN', however, when printing the updates_df where it multiplies the 'Grade' column by 100 to convert to percentage, the value 'NaN' being a string, had actually been multiplied by 100, giving me 100 'NaN' in a row (I had fun with it and made it a beat upon realizing, nannannannannannannan)


```python
data_mistake = {"Due_Date": ['2020-10-2', '2020-10-7', '2020-12-6', '2020-11-9',
                             '2020-9-26', '2020-12-1'],
               'Time': [23.59,12.00,23.59,23.59,7.00,10.00], 
               'Class_Name': ['a', 'b', 'c', 'd', 'e', 'c'], 
               'Course_Code': ['NESC 1', 'NESC 2', 'NESC 3', 'NESC 4', 'NESC 5', 
                               'NESC 3'], 
               'Assignment_Type': ['Reading', 'Exam', 'Discussion' 'post', 'Demo',
                                   'Test', 'Project' ], 
               'To_Do': ['Ch.1, Ch. 2', 'Ch. 7, Ch.9(p.333-335)', 'Lecture 1 & 2', 
                         'Find relevant topic', 'Ch.1 & Ch.2-2.5', 
                         'course material application'], 
               'Complete?': [1, 0, 0, 0, 1, 0],
               'Grade_mistake': ['NaN', 0, 0, 0, 45/48, 0]}

data_mistake_df = pd.DataFrame(data_mistake, columns = ['Due_Date', 'Time', 
                                                        'Class_Name', 'Course_Code',
                                                        'Assignment_Type', 'To_Do', 
                                                        'Complete?', 'Grade_mistake'])

print(data_mistake_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    0  2020-10-2  23.59          a      NESC 1         Reading   
    1  2020-10-7  12.00          b      NESC 2            Exam   
    2  2020-12-6  23.59          c      NESC 3  Discussionpost   
    3  2020-11-9  23.59          d      NESC 4            Demo   
    4  2020-9-26   7.00          e      NESC 5            Test   
    5  2020-12-1  10.00          c      NESC 3         Project   
    
                             To_Do  Complete? Grade_mistake  
    0                  Ch.1, Ch. 2          1           NaN  
    1       Ch. 7, Ch.9(p.333-335)          0             0  
    2                Lecture 1 & 2          0             0  
    3          Find relevant topic          0             0  
    4              Ch.1 & Ch.2-2.5          1        0.9375  
    5  course material application          0             0  



```python
data_mistake_df['Grade_mistake']=data_mistake_df['Grade_mistake']*100
print(data_mistake_df)
```

        Due_Date   Time Class_Name Course_Code Assignment_Type  \
    0  2020-10-2  23.59          a      NESC 1         Reading   
    1  2020-10-7  12.00          b      NESC 2            Exam   
    2  2020-12-6  23.59          c      NESC 3  Discussionpost   
    3  2020-11-9  23.59          d      NESC 4            Demo   
    4  2020-9-26   7.00          e      NESC 5            Test   
    5  2020-12-1  10.00          c      NESC 3         Project   
    
                             To_Do  Complete?  \
    0                  Ch.1, Ch. 2          1   
    1       Ch. 7, Ch.9(p.333-335)          0   
    2                Lecture 1 & 2          0   
    3          Find relevant topic          0   
    4              Ch.1 & Ch.2-2.5          1   
    5  course material application          0   
    
                                           Grade_mistake  
    0  NaNNaNNaNNaNNaNNaNNaNNaNNaNNaNNaNNaNNaNNaNNaNN...  
    1                                                  0  
    2                                                  0  
    3                                                  0  
    4                                              93.75  
    5                                                  0  


However, found that when applying the function float() to 'NaN', the value remained the same:


```python
A=float("NaN")
print(type(A))
print(A*100)
```

    <class 'float'>
    nan



```python

```
