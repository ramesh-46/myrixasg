
1. Given a sorted array of positive and negative numbers. You have to Square it and sort it. Constraint : Time complexity O(n) 
Example: 
Input: [-12, -8 , -7, -5, 2, 4, 5, 11, 15] 
Output : [4, 16, 25, 25, 49, 56, 121, 144, 225] 


def square_and_sort(nums):
    return sorted(num ** 2 for num in nums)

# Test case
numbers = [-12, -8, -7, -5, 2, 4, 51, 11, 15]
print(square_and_sort(numbers))







2. Design an immutable class with following attributes 
String name; 
String Id, 
Date dateOfJoining 
List<Address> addresses; 


from typing import List, NamedTuple
from datetime import date

class Location(NamedTuple):
    line: str
    town: str
    province: str
    postal_code: str

class FixedEmployeeDetails(NamedTuple):
    full_name: str
    employee_id: str
    joining_date: date
    residences: List[Location]

# Example usage
loc1 = Location("789 Maple Ave", "Riverdale", "CA", "90210")
loc2 = Location("101 Oak St", "Riverdale", "CA", "90211")
employee = FixedEmployeeDetails("Alice Johnson", "EMP456", date(2019, 3, 10), [loc1, loc2])

print(employee)





3. Given an array of Red Green Blue balls.You have to sort it. 
Constraint : Time complexity O(n) 
Constraint : Space complexity O(1) 
Example: 
Input: [R, G, B, G, G, R, B, B, G] 
Output : [B,B,B,G,G,G,G,R, R] 



def arrange_colors(colors):
    colors.sort(key=lambda color: {'B': 0, 'G': 1, 'R': 2}[color])

# Example usage
palette = ['R', 'G', 'B', 'R', 'G', 'R', 'B', 'B', 'G']
arrange_colors(palette)
print(palette)









4. We are given two arrays that represent the arrival and departure times of trains, the task is to find the minimum number of platforms required so that no train waits. 
Examples: 
Input: arr[] = {9:00, 9:40, 9:50, 11:00, 15:00, 18:00}, dep[] = {9:10, 12:00, 11:20, 11:30, 19:00, 20:00} 
Output: 3 
Explanation: There are at-most three trains at a time (time between 9:40 to 12:00) 
Input: arr[] = {9:00, 9:40}, dep[] = {9:10, 12:00} 
Output: 1 
Explanation: Only one platform is needed. 



from datetime import datetime

def min_stations_needed(arrivals, departures):
    arr = sorted([datetime.strptime(t, '%H:%M') for t in arrivals])
    dep = sorted([datetime.strptime(t, '%H:%M') for t in departures])
    
    platforms = 0
    max_needed = 0
    i = j = 0
    while i < len(arrivals):
        if arr[i] < dep[j]:
            platforms += 1
            i += 1
        else:
            platforms -= 1
            j += 1
        max_needed = max(max_needed, platforms)
    
    return max_needed

# Example usage
start = ["09:00", "09:40", "09:50", "11:00", "15:00", "18:00"]
end = ["09:10", "12:00", "11:20", "11:30", "19:00", "20:00"]
print(min_stations_needed(start, end))








5. Sort hashmap by value. 
Example: 
Input: Map: {101=John Doe, 102=Jane Smith, 103=Peter Johnson} 
output: Map: {102=Jane Smith, 101=John Doe, 103=Peter Johnson}



def sort_dict_by_value(d):
    return dict(sorted(d.items(), key=lambda x: x[1]))

# Example usage
data = {101: "John Doe", 102: "Jane Smith", 107: "Peter Johnson"}
print(sort_dict_by_value(data))




