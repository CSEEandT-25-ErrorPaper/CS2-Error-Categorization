# Task 1: Weather Report

Create a class `Forecast`, which can analyze data from multiple weather stations and generate a weather forecast.

### Constructor
`CONSTRUCTOR(int[][] rainfall, String[] descriptors)`

A constructor that accepts two parameters: 
- `rainfall`: a 2D integer array representing rainfall data.
- `descriptors`: a string array containing general weather reports for the day.

In the `rainfall` array, each row corresponds to a weather station, and each column represents a day.

In the `descriptors` array, each column represents a day and contains one of the values: "sunny," "rainy," or "thunderstorm."

#### Example:

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | -10   | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | -6    | 57    | 8     | 10    | -100  | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    |

| Day 1   | Day 2   | Day 3       | Day 4   | Day 5   | Day 6       | Day 7   |
|---------|---------|-------------|---------|---------|-------------|---------|
| sunny   | rainy   | thunderstorm| sunny   | sunny   | thunderstorm| sunny   |

### Data Preparation
`dataPreparation()`

The rainfall data may contain erroneous negative values. This method should clean the data according to the following rules:
- If the descriptor for a day is "sunny," replace negative values with 0.
- If the descriptor is "rainy," replace negative values with the average of all positive values from other weather stations for that day. If all stations report errors, set the values to 0.
- If the descriptor is "thunderstorm," replace negative values with their absolute value.

#### Example after `dataPreparation`:

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | 0     | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | 21    | 57    | 8     | 10    | 100   | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    |

### Total Rainfall
`totalRainfall()`

This method calculates the total rainfall measured by all weather stations during the observation period.

#### Example:
For the given data, the total rainfall is 683.

### Rainfall Query
`getRainfall(int day_index, String mode)`

This method receives a day index and a mode as parameters. If the index is invalid, return -1. The mode can be either "biggest," "lowest," or "sum."
- "lowest" returns the lowest rainfall value of the day.
- "biggest" returns the highest rainfall value of the day.
- "sum" returns the sum of rainfall for the day.

#### Examples:
- `getRainfall(0, "lowest")` → returns 0
- `getRainfall(3, "biggest")` → returns 39
- `getRainfall(4, "sum")` → returns 85
- `getRainfall(7, "sum")` → returns -1

### Temperature Calculation
`calculateTemperature()`

This method determines the temperature per day for each weather station. The temperature is calculated as follows:
- If the weather is "sunny," multiply the rainfall by 3 to get the temperature.
- If the weather is "rainy," divide the rainfall by 2 to get the temperature.
- If the weather is "thunderstorm," return the remainder of dividing the rainfall by the current day index. If the day index is 0, divide the rainfall by the number of stations.

#### Example:

| Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|-------|-------|-------|-------|-------|-------|-------|
| 0     | 11    | 1     | 57    | 135   | 0     | 60    |
| 105   | 10    | 1     | 24    | 30    | 0     | 30    |
| 45    | 10    | 1     | 117   | 90    | 0     | 60    |

### Trend Calculation
`trend(int n)`

This method creates a forecast based on the average rainfall per station and day for the last `n` days. It returns a string corresponding to one of the descriptors:
- If the average rainfall over the last `n` days is below 50, return "sunny."
- If the average rainfall is 50 or higher, return "rainy."
- If the average rainfall is exactly 75, return "thunderstorm."

#### Examples:
- `n = 3` → The average rainfall over the last 3 days is 42. Return "sunny."
- `n = 2` → The average rainfall over the last 2 days is 50. Return "rainy."

# Task 2: University Network

Create classes for managing a university network, including students, courses, lecturers, and universities.

### Student
`Student(String first_name, String surname, String email, String studentID)`

The constructor creates a student with the specified values.

#### Methods:
- `addCourse(Course course, String grade)`: Adds a course to the student. If the course already exists, the grade is overwritten. If the new grade is "5.0," increment the number of failed attempts.
- `getFirstName()`: Returns the first name.
- `getSurname()`: Returns the surname.
- `getEmail()`: Returns the email.
- `getStudentID()`: Returns the student ID.
- `getCourses()`: Returns a list of courses.
- `getGradeInCourse(Course course)`: Returns the grade for the given course, or `None` if it does not exist.
- `getNumberOfFailedAttempts(Course course)`: Returns the number of failed attempts for the course, or `None` if the course does not exist.
- `getReachedCP()`: Returns the number of credit points (CP) for passed courses.
- `getAverageGrade()`: Returns the average grade, excluding "5.0." Grades are weighted by credit points.

### Docent
`Docent(String first_name, String surname, String email)`

The constructor creates a lecturer with the specified values.

#### Methods:
- `getFirstName()`: Returns the first name.
- `getSurname()`: Returns the surname.
- `getEmail()`: Returns the email.
- `addCourse(String course_name)`: Adds a course that the lecturer can teach.
- `getCourses()`: Returns a list of courses the lecturer can teach.

### Course
`Course(String name, int cp)`

The constructor creates a course with the given name and credit points.

#### Methods:
- `getName()`: Returns the course name.
- `getCP()`: Returns the credit points.
- `setDocent(Docent docent)`: Sets the lecturer for the course. Returns `True` if successful, `False` otherwise.
- `removeDocent()`: Removes the lecturer from the course.
- `getDocent()`: Returns the current lecturer, or `None` if not set.

### University
`University(String name)`

The constructor creates a university with the specified name.

#### Methods:
- `addDocent(Docent docent)`: Adds a lecturer to the university. Returns `True` if successful, `False` otherwise.
- `getDocent(String first_name, String surname)`: Returns the lecturer with the given name, or `None` if not found.
- `getListOfDocents()`: Returns a list of lecturers.
- `addCourse(String course_name, int cp)`: Adds a new course to the university and returns it.
- `getCourse(String course_name)`: Returns the course with the specified name, or `None` if not found.
- `getListOfCourses()`: Returns a list of courses.
- `getListOfEmptyCourses()`: Returns a list of courses without lecturers.
- `addStudent(String first_name, String surname, String email)`: Adds a student to the university. Student IDs are generated sequentially.
- `removeStudent(Student student)`: Removes a student. Returns `True` if successful, `False` otherwise.
- `getStudent(String first_name, String surname)`: Returns the student with the given name, or `None` if not found.
- `getListOfStudents()`: Returns a list of students.
- `distributeCourses()`: Assigns lecturers to courses, ensuring an even distribution of courses among lecturers.
- `getStudentsByGrade(List<Course> courses)`: Returns a list of students sorted by average grade, filtered by the specified courses.
- `getAverageGradeOfCourse(Course course)`: Returns the average grade of the course, excluding "5.0."
- `getCoursesByFailureRate()`: Returns a list of courses sorted by failure rate.

### University Network
`UniversityNetwork()`

The constructor creates an empty university network.

#### Methods:
- `registerUniversity(University university)`: Adds a university to the network. Returns `True` if successful, `False` otherwise.
- `getUniversityByStudentCount()`: Returns a list of universities sorted by student count.
- `getUniversityByCoveredCourses()`: Returns a list of universities sorted by the number of courses with assigned lecturers.

---

# Task 3: Bank System with Double Linked List

Create a double linked list that represents a bank system. Each node represents an account.

### Account
`Account(String firstName, String surname, String phoneNumber, int balance)`

The constructor initializes the attributes of the account.

#### Methods:
- `getPrev()`: Returns the previous account.
- `getNext()`: Returns the next account.
- `setPrev(Account account)`: Sets the previous account.
- `setNext(Account account)`: Sets the next account.

### Bank
`Bank()`

The constructor creates an empty list of accounts.

#### Methods:
- `getHead()`: Returns the first account.
- `append(String firstName, String surname, String phoneNumber, int balance)`: Adds a new account at the end.
- `get(int index)`: Returns the account at the specified index, or `null` if the index is invalid.
- `insert(int index, String firstName, String surname, String phoneNumber, int balance)`: Inserts a new account at the specified index. Returns `True` if successful, `False` otherwise.
- `delete(int index)`: Deletes the account at the specified index. Returns `True` if successful, `False` otherwise.
- `search(int mode, String value)`: Searches for the first account that matches the specified `value` based on the `mode`.
- `printAccounts()`: Prints all accounts.
- `swap(int index1, int index2)`: Swaps the accounts at the specified indices. Returns `True` if successful, `False` otherwise.
- `deleteSublist(int startIndex, int accountsToDelete)`: Deletes a sublist of accounts starting at `startIndex`. Returns the remaining list.
- `sort(int mode, int orderKind)`: Sorts the accounts based on the specified `mode` and `orderKind`.
- `getMedian()`: Returns the median balance.
- `deleteSublistSuccessive(int total)`: Deletes successive sublists where the sum of balances equals the specified `total`.
- `removeDuplicates(int mode, String value)`: Removes duplicate accounts, keeping only the first occurrence.
- `fuse(Bank secondBank)`: Merges two banks. If an account exists in both banks, the balances are added, and the duplicate is removed from the second bank.

---

# Task 4: Restaurant Ordering System with Priority Queue

Model a restaurant system with multiple orders and execution units (cooks). Each order has an ID, description, priority, arrival time, and execution time.

### Order
`Order(int id, String description, int priority, int arrivalTime, int executionTime)`

The constructor initializes the order with the specified values.

#### Methods:
- `getID()`: Returns the order ID.
- `getDescription()`: Returns the order description.
- `getArrivalTime()`: Returns the arrival time.
- `getExecutionTime()`: Returns the execution time.
- `getPriority()`: Returns the priority.

### Node
`Node(Order order)`

The constructor creates a node that stores an order.

#### Methods:
- `getPrev()`: Returns the previous node.
- `getNext()`: Returns the next node.
- `setPrev(Node prev)`: Sets the previous node.
- `setNext(Node next)`: Sets the next node.

### List
`List()`

The constructor creates an empty list of nodes.

#### Methods:
- `append(Node node)`: Appends a node to the list. Returns `True` if successful, `False` otherwise.
- `insert(int index, Node node)`: Inserts a node at the specified index. Returns `True` if successful, `False` otherwise.
- `remove(int index)`: Removes the node at the specified index. Returns `True` if successful, `False` otherwise.
- `swap(int first_index, int second_index)`: Swaps two nodes. Returns `True` if successful, `False` otherwise.
- `sort()`: Sorts the list in descending order of priority.
- `getMostUrgentOrder()`: Returns the most urgent order and removes it from the list.

### Restaurant
`Restaurant(int executionUnits)`

The constructor initializes a restaurant with the specified number of execution units (cooks).

#### Methods:
- `addOrder(int id, String description, int priority, int arrivalTime, int executionTime)`: Adds an order to the list. Returns `True` if successful, `False` otherwise.
- `removeOrder(int id)`: Removes the order with the specified ID. Returns `True` if successful, `False` otherwise.
- `getKMostUrgentOrders(int k)`: Prints the `k` most urgent orders in descending priority.
- `execute()`: Starts executing orders. Returns a list of lists where each inner list represents the orders being processed at a given time by each cook.

---

# Task 5: CPU with Binary Search Tree

Model a CPU using a binary search tree where each process is represented as a node.

### Process
`Process(int id, String category)`

The constructor initializes a process with the specified ID### Process
`Process(int id, String category)`

The constructor initializes a process with the specified ID and category.

#### Methods:
- `getID()`: Returns the process ID.
- `setID(int id)`: Sets the process ID.
- `getCategory()`: Returns the process category.
- `setCategory(String category)`: Sets the process category.
- `getLeft()`: Returns the left child process.
- `setLeft(Process left)`: Sets the left child process.
- `getRight()`: Returns the right child process.
- `setRight(Process right)`: Sets the right child process.

### Processor
`Processor()`

The constructor creates an empty binary search tree representing the CPU.

#### Methods:
- `getProcess(int id)`: Returns the process with the specified ID. Throws an exception if the ID is not found.
- `getCategory(int id)`: Returns the category of the process with the specified ID. Throws an exception if the ID is not found.
- `insert(int id, String category)`: Adds a new process to the tree. Throws an exception if the ID is invalid or already exists.
- `delete(int id)`: Deletes the process with the specified ID. Throws an exception if the ID is invalid or not found.
- `getProcessesByCategory(String category)`: Returns a list of processes that belong to the specified category.
- `getProcessesById(int lowerBound, int upperBound)`: Returns a list of processes with IDs between `lowerBound` and `upperBound`.
- `toInorderList()`: Returns a list of processes in an inorder traversal.
- `leftView()`: Returns a list of process IDs that are the leftmost nodes at each level.
- `maxRootToLeafPath()`: Returns the longest path from the root to a leaf.
- `height()`: Returns the height of the processor tree.
- `smallestGreaterKey(Process current, String category)`: Finds the smallest process larger than the current process and belongs to the specified category.
- `findKthSmallest(int k)`: Finds and returns the k-th smallest process in the tree.
- `areIdentical(Processor otherProcessor)`: Checks if another processor tree is identical to the current tree.
- `getCommonAncestor(Process firstProcess, Process secondProcess)`: Returns the common ancestor of two processes.
- `getLeafCount()`: Returns the number of leaf nodes in the tree.
- `invert()`: Inverts the processor tree, placing smaller processes on the right side instead of the left.

---

# Task 6: Graph Implementation for Energy Networks

Model an undirected graph where each node represents a location with x and y coordinates. Each edge is a bidirectional connection between nodes.

### Graph
`Graph()`

The constructor creates an empty graph.

#### Methods:
- `newNode(int x, int y)`: Adds a new node to the graph with the specified coordinates. Returns a unique number for the node. If the node already exists, returns -1.
- `setEdge(int from, int to)`: Creates an edge between two nodes. Returns `True` if successful, `False` otherwise.
- `getEdges()`: Returns a list of lists, where each sublist contains the nodes connected to the i-th node.
- `getNGons(int n)`: Returns a list of disjoint n-gons (cycles) found in the graph.
- `getLongestPath(int from, int to)`: Returns the longest path between two nodes. If no path exists, returns an empty list.
- `getNonCrossingGraph()`: Returns a new graph without intersecting edges. Intersection points are replaced with new nodes.

#### Example:
```python
graph = Graph()
graph.newNode(0, 0)  # returns 0
graph.newNode(5, 5)  # returns 1
graph.newNode(5, 0)  # returns 2
graph.newNode(0, 5)  # returns 3
graph.setEdge(0, 1)  # returns True
graph.setEdge(0, 2)  # returns True
graph.setEdge(1, 3)  # returns True
graph.getEdges()     # returns [[1, 2], [0, 3], [0], [1]]
