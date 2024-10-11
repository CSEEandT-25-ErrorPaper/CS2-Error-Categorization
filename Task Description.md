
# Task 1: Weather Report

Create a class `Forecast`, which can analyze data from multiple weather stations and generate a weather forecast.

### `Constructor Forecast(int[][] rainfall, String[] descriptors)`
A constructor in the corresponding programming language, which receives the weather station data in two parameters. The first parameter is the rainfall data, given as a two-dimensional integer array rainfall, and the second parameter is the general weather report of the day, provided as a descriptive string in a string array descriptors.

In the ```rainfall``` array, each row corresponds to a weather station, and each column represents a day.

In the descriptors array, each column also represents a day, with each entry being one of the values: **"sunny"**, **“rainy”**, or **“thunderstorm”**.

#### Example:

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | -10   | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | -6    | 57    | 8     | 10    | -100  | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    

Table 1: Rainfall data from 3 weather stations over a period of 7 days

| Day 1   | Day 2   | Day 3       | Day 4   | Day 5   | Day 6       | Day 7   |
|---------|---------|-------------|---------|---------|-------------|---------|
| sunny   | rainy   | thunderstorm| sunny   | sunny   | thunderstorm| sunny   |

Table 2: Weather reports for the corresponding 7 days

### `dataPreparation()`

The rainfall data may contain errors, including negative values. This method should process the rainfall data so that it can be reused later. Any erroneous (negative) data must be handled according to the following specifications:

- If the descriptor for the corresponding day is **"sunny"**, the negative value should be replaced with `0`.
- If the descriptor for the corresponding day is **"rainy"**, the negative value should be replaced by the average of all (positive) values from the other weather stations for that day. Use whole numbers for calculations. If all the stations' data for that day are erroneous, set the value for all stations to `0`.
- If the descriptor for the corresponding day is **"thunderstorm"**, the negative value should be replaced by its corresponding absolute value.

**Example**: This is how the example data mentioned above should look after modification by the method `dataPreparation`. Changes are marked in <span style="color:red">red</span>.

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | **0**     | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | **21**    | 57    | 8     | 10    | **100**   | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    |

Table 3: Rainfall after ```dataPreparation()```

### `totalRainfall()`

This method calculates the total rainfall measured by the weather stations during the measurement period. 
#### Example:
With the given example data, the total rainfall is **683**.

### `getRainfall(int day_index, String mode)`
This method receives the index of the day in the array/list `rainfall` and a `mode` as parameters. If an invalid `day_index` is passed, return `-1`. The `mode` can be either "biggest", "lowest", or "sum".

- If the `mode` for the corresponding day is **"lowest"**, the method will return the lowest value for that day.
- If the `mode` for the corresponding day is **"biggest"**, the method will return the highest value for that day.
- If the `mode` for the corresponding day is **"sum"**, the method will return the sum of the rainfall for that day.

#### Examples:
- `getRainfall(0, "lowest")` → returns 0
- `getRainfall(3, "biggest")` → returns 39
- `getRainfall(4, "sum")` → returns 85
- `getRainfall(7, "sum")` → returns -1

### `calculateTemperature()`
This method determines the temperature per day for each weather station and returns it as a two-dimensional array/list. The temperature is calculated as follows:
- If the weather report for the specified day is **sunny**, triple the rainfall amount to get the temperature.
- If the weather report for the specified day is **rainy**, reduce the rainfall amount by half to get the temperature.
- If the weather report for the specified day is **thunderstorm**, return the remainder of the division of the rainfall by the current day index. If the day index is `0`, divide the rainfall amount by the number of weather stations.

#### Example:

| Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|-------|-------|-------|-------|-------|-------|-------|
| 0     | 11    | 1     | 57    | 135   | 0     | 60    |
| 105   | 10    | 1     | 24    | 30    | 0     | 30    |
| 45    | 10    | 1     | 117   | 90    | 0     | 60    |

**Table 4**: Return of `calculateTemperature()`

### `trend(int n)`
This method creates a forecast based on the average rainfall per station and day over the last `n` days. The forecast is returned as a string corresponding to one of the established descriptors.

- If the average rainfall over the last `n` days is below 50, return **"sunny"**.
- If the average rainfall over the last `n` days is 50 or higher, return **"rainy"**.
- In the special case where the average rainfall over the last `n` days is exactly 75, return **"thunderstorm"**.

#### Examples:
- `n = 3` → The average rainfall over the last 3 days = (45+75+20+10+100+10+30+75+20)/9 = 42  → Return **"sunny"**
- `n = 2` → The average rainfall over the last 2 days = (75+20+100+10+75+20)/6 = 50 → Return **"rainy"**

# Task 2: University Network
### Task

Create classes for managing a university network.
Classes should be created for students, courses, professors, and universities.

A student is uniquely identified by their matriculation number (1-999). Additionally, a student has a first name, a last name, and an email. Furthermore, a student should have a collection of courses. These courses should internally be stored as either “passed” or “not passed”. Additionally, it should be recorded how many failed attempts the student has had in a particular course. For the latest exam, the grade should be stored, and a 5.0 should indicate “not passed”.

A course should have a title, a number of credits, and a professor.

A professor should have a first name, a last name, and an email. A professor should also have a list of possible courses they teach.

A university should be a collection of students, professors, and courses. Additionally, a university should have a name.

The university network should be a collaboration of multiple universities. Implement the following classes and methods:


### Student
`Student(String firstName, String surname, String email, String studentID)`
Which corresponds to the constructor of your chosen language and creates a student with the generated values.

### `addCourse(Course course, String grade)`
 Adds a course to the student. If the course already exists, the grade is overwritten. If the new grade is "5.0," increment the number of failed attempts.


### `getFirstName()`
Which returns the first name.

### `getSurname()`
Which returns the surname.

### `getEmail()`
Which returns the email.

### `getStudentID()`
Which returns the matriculation number.

### `getCourses()`
Which returns the list of enrolled courses.

### `getGradeInCourse(Course course)`
Which returns the grade in the specified course. If the course does not exist, return `None`/`null`.

### `getNumberOfFailedAttempts(Course course)`
Which returns the number of failed attempts in the respective course. If the course does not exist, return `None`/`null`.

### `getReachedCP()`
Which returns the number of credit points earned from passed courses.

### `getAverageGrade()`
Which calculates and returns the average grade, excluding "5.0". The grades should be weighted according to the credit points of the courses. The more credit points a course offers, the more influence its grade has on the average grade.

### Docent

### `Docent(String first_name, String surname, String email)`
Which corresponds to the constructor of your chosen language and creates a docent with the generated values.

### `getFirstName()`
Which returns the first name.

### `getSurname()`
Which returns the surname.

### `getEmail()`
Which returns the email.

### `addCourse(String course_name)`
Which allows the docent to offer courses with the given name.

### `getCourses()`
Which returns a list of course names the docent can teach.

### Course

### `Course(String name, int cp)`
Which corresponds to the constructor of your chosen language and creates a course with the generated values.

### `getName()`
Which returns the name of the course.

### `getCP()`
Which returns the number of credit points that can be earned in this course.

### `setDocent(Docent docent)`
Which sets the docent for the course, replacing any existing one if present. This should only be done if the docent is able to teach this course. If the docent is set, return `True`, otherwise return `False`.

### `removeDocent()`
Which removes the current docent from the course.

### `getDocent()`
Which returns the docent for the course if one is set, otherwise `None`/`null`.

### University
### `University(String name)`
Which corresponds to the constructor of your chosen language and creates a university with the generated values.

### `addDocent(Docent docent)`
Which adds the given docent to the university. If this docent is already at the university, return the boolean value `False`, otherwise return `True`.

### `getDocent(String first_name, String surname)`
Which returns the docent with the corresponding name. If no docent with this name exists, return `None`/`null`.

### `getListOfDocents()`
Which returns a list of docents.

### `addCourse(String course_name, int cp)`
Which creates a new course at the university and returns it.

### `getCourse(String course_name)`
Which returns the course with the corresponding name. If no course with this name exists, return `None`/`null`.

### `getListOfCourses()`
Which returns a list of courses.

### `getListOfEmptyCourses()`
Which returns a list of courses that have no docent assigned.

### `addStudent(String first_name, String surname, String email)`
Which adds a student to the university. A `Student` object should be created, and the matriculation number should be assigned as a consecutive number starting from 1. The matriculation number should always have six digits. If the number does not have six digits, fill it with leading zeros.

### `removeStudent(Student student)`
Which unenrolls the student. If the student exists and was unenrolled, return `True`, otherwise return `False`.

### `getStudent(String first_name, String surname)`
Which returns the student with the corresponding name. If no student with this name exists, return `None`/`null`.

### `getListOfStudents()`
Which returns a list of students.

### `distributeCourses()`
Which assigns docents to the respective courses. It should take into account which courses a docent can teach. Additionally, a single docent should be assigned as few courses as possible. If there are two docents who can teach a course, the docent with fewer courses should be selected. Before the calculation, all docents should be removed from the courses.

### `getStudentsByGrade(List<Course> courses)`
Which returns a list of students sorted by their average grade. Only students who are enrolled in one of the courses from the `courses` list should be considered.

### `getAverageGradeOfCourse(Course course)`
Which calculates and returns the average grade for the course. Grades of "5.0" should not be included in the calculation.

### `getCoursesByFailureRate()`
Which returns a list of courses sorted in descending order based on their failure rate.

### University Network
### `UniversityNetwork()`
Which corresponds to the constructor of your chosen language and creates an empty university network.

### `registerUniversity(University university)`
Which adds a university to the network. If this university is already in the network, return the boolean value `False`, otherwise return `True`.

### `getUniversityByStudentCount()`
Which returns a list of universities, sorted in descending order based on the number of enrolled students.

### `getUniversityByCoveredCourses()`
Which returns a list of universities, sorted in descending order based on the number of courses that have an assigned docent.

---

# Task 3: Bank System

Create a doubly linked list that can be used as a bank. The nodes of the list should be represented by the class `Account`. Each node in the list should contain not only the previous and next nodes but also the data of an account, including the first name, last name, phone number, and current account balance.

Important: You are required to manually implement your own data structure and not use the already available lists from the standard library. Submissions that simply “repackage” the existing lists will not be counted.

Implement the following for the `Account` class:
### Account
### `constructor(String firstName, String name, String phoneNumber, int balance)`
Which corresponds to the constructor of your chosen language and sets the attributes of the node to `firstName`, `name`, `phoneNumber`, and `balance`. The previous and next nodes should be initialized to `null` or the equivalent `None`.

### `getPrev()`
Which returns the previous account.

### `getNext()`
Which returns the next account.

### `setPrev(Konto konto)`
Which sets the given account as the previous one. If the original account already had a previous account, those should be set as the previous account of the given one.

### `setNext(Konto konto)`
Which sets the given account as the next one. If the original account already had a next account, those should be set as the next account of the given one.

Implement the following for the `Bank` class:
### Bank

### `constructor()`
Which corresponds to the constructor of your chosen language and creates an empty list.

### `getHead()`
Returns the head of the list (the first element).

### `append(String firstName, String name, String phoneNumber, int balance)`
Adds a new account to the bank at the last position.

### `get(int index)`
Which returns the account at the given index. If the index is not present in the list, return `null` or `None`.

### `insert(int index, String firstName, String name, String phoneNumber, int balance)`
Which creates a new account with the given values and adds it at the specified index. If the passed index matches the current size of the list, the new account is added at the end of the list.
If the addition is successful, return `True`, otherwise return `False`.

### `delete(int index)`
Which deletes the account at the specified index. If the account is successfully deleted, return `True`, otherwise return `False`.

### `search(int mode, String value)`
Which searches for the account with the first occurrence of the given value according to the passed mode and returns the account.
The `mode` parameter can take values from 0-3, which correspond to the following meanings:
- 0 = `firstName`
- 1 = `name`
- 2 = `phoneNumber`
- 3 = `bankBalance`

If `mode` is 0, the `value` refers to the first name of the account holder. The method should return the first account where `firstName` matches the given `value`.

### `printAccounts()`
Which prints all accounts in the bank to the console. Ensure that the account data is formatted in a readable manner.

### `swap(int index1, int index2)`
Which swaps two accounts at the given indices in the bank. If the swap is successful, return `True`, otherwise return `False`.

### `deleteSublist(int startIndex, int accountsToDelete)`
Which deletes a number of accounts, specified by `accountsToDelete`, from the bank starting at `startIndex`, inclusive. Return the remaining list after the deletion.

### `sort(int mode, int orderKind)`
Which sorts the accounts based on the given parameters. The `mode` parameter determines by which account attribute the list is sorted. The possible values of `mode` are the same as those in the `search` method. The `orderKind` parameter can take values of 0 or 1, indicating whether the list should be sorted in ascending or descending order:
- 0 = ascending
- 1 = descending

Example: `sort(1, 1)`
→ The list is sorted in descending alphabetical order by last name.

### `getMedian()`
Which determines the median of the account balances. The median is the value that lies exactly in the middle of a sorted list. If the number of accounts is odd, the median is the `balance` of the account in the middle of the list. If the number of accounts is even, there is no unique middle value, and the median is the average of the two middle values.

### `deleteSublistSuccessive(int total)`
Deletes all consecutive sublists whose balances sum up to the given `total`, one after another.

Example: 
Given the list `[6, 7, 3, 4, 8, 9, 2]`, calling `deleteSublistSuccessive(10)` would result in:
- After the 1st iteration: `[6, 4, 8, 9, 2]` (7 and 3 were deleted)
- After the 2nd iteration: `[8, 9, 2]` (6 and 4 were deleted)

### `removeDuplicates(int mode, String value)`
Which deletes all accounts that are duplicates based on the given `value` and `mode`, except for the first occurrence. The possible values for `mode` are the same as in the `search` and `sort` methods.

### `fuse(Bank secondBank)`
Which merges two banks. If two accounts have identical first name, last name, and phone number, add their balances together and remove the account that belongs to the second bank (the bank passed as an argument).
### Memory Aid
#### `mode`
- 0 = `firstName`
- 1 = `name`
- 2 = `phoneNumber`
- 3 = `bankBalance`

#### `orderKind`
- 0 = ascending
- 1 = descending

### Note for Java
If the passed `mode` is 3, you can use `Integer.parseInt()` to convert the string into an integer. 

Example:
```java
String value = "123";
int intValue = Integer.parseInt(value);
```


---

# Task 4: Restaurant Ordering System
### Task
Priority queues are frequently used in scheduling applications. One example of such an application is a restaurant that evaluates and processes its orders based on various parameters. The restaurant, which in our case is simplified to consist of multiple execution units (the chefs), can accept and fulfill a variety of orders.

In this task, an order should consist of a unique “ID”, a “description” of the associated dish, and a “priority”. Additionally, for each order, the “arrivalTime” and “executionTime” should be stored.

The restaurant should have the ability to consist of multiple “executionUnits” (so that several orders can be processed simultaneously). The “arrivalTime” describes the discrete point in time when the processing (preparation) of an order can start. The “executionTime” describes how many discrete time steps are needed to complete the order. The “priority” attribute indicates which order should be preferred. A higher number means that the preparation of this order takes precedence. If multiple “executionUnits” are available for execution, the order with the highest priority should be prepared.

Please implement the following classes and methods:

### Order

This class should represent an order. The following methods are required:

### `Order(int id, String description, int priority, int arrivalTime, int executionTime)`
Implement a constructor, which sets the attributes of the order based on the passed values.

### `int getID()`
Which returns the ID of the order.

### `String getDescription()`
Which returns the description of the order. The description can, for example, be the dish being prepared as a string.

### `int getArrivalTime()`
Which returns the arrival time of the order.

### `int getExecutionTime()`
Which returns the execution time of the order.

### `int getPriority()`
Which returns the priority of the order.

### Node
This class should be used to store an order in a doubly linked list. Please implement the following methods:

### `Node(Order order)`
Which corresponds to the constructor of your chosen language. This should take an order as an argument and set the node's attribute accordingly.

### `Node getPrev()`
Which returns the previous node.

### `Node getNext()`
Which returns the next node.

### `void setPrev(Node prev)`
Which sets the previous node to `prev`.

### `void setNext(Node next)`
Which sets the next node to `next`.

### List
This class should be used to store various orders in a doubly linked list. The following methods are required:

### `List()`
Which corresponds to the constructor of your chosen language and creates an empty list.

### `boolean append(Node node)`
Which appends the node `node` to the list. The method should return `true` if the append operation was successful, otherwise it should return `false`.

### `boolean insert(int index, Node node)`
Which inserts the node `node` at the index `index`. The method should return `true` if the insertion was successful, otherwise it should return `false`.

### `boolean remove(int index)`
Which removes the node at the index `index` from the list. The method should return `true` if the removal was successful, otherwise it should return `false`.

### `boolean swap(int first_index, int second_index)`
Which swaps the node at index `first_index` with the node at index `second_index` in the list. The method should return `true` if the swap was successful, otherwise it should return `false`.
Note: Pay special attention to edge cases, e.g., when two nodes are directly next to each other.

### `void sort()`
Which sorts the list in descending order based on the priority of the orders. You may choose the sorting algorithm.

### `Order getMostUrgentOrder()`
Which returns the order with the highest priority and removes the respective node from the list.

### Restaurant

This class should model a restaurant. A restaurant should have "executionUnits" (chefs) and store a doubly linked list of orders. Please implement the following methods:

### `Restaurant(int executionUnits)`
Which initializes a restaurant with `executionUnits` chefs and an empty order list.

### `boolean addOrder(int id, String description, int priority, int arrivalTime, int executionTime)`
Which adds an order to the restaurant's order list. Note that the ID of each order must be unique. If the given ID already exists in the list, the new order should not be added. If the insertion was successful, return `true`, otherwise return `false`.

### `boolean removeOrder(int id)`
If there is an order in the order list with the ID `id`, it should be deleted. If the order is deleted, the method should return `true`, otherwise return `false`.

### `void getKMostUrgentOrders(int k)`
Which prints the data of the top `k` highest-priority orders in the restaurant. The output should be in descending order of priority. For each order, the following format should be used: `"id, description, priority"`. If `k` is greater than the length of the list, an error message should be displayed.

### `List execute()`
When this method is called, the preparation of the orders should begin (starting at time 0, progressing positively). All chefs in the restaurant should work to complete all orders. At each time step, the highest-priority orders should be worked on. If higher-priority orders come in during the execution of an order, the current order should not be interrupted.

The execution is considered complete when all orders are finalized. To track the correct execution of orders, the method should return a list of lists at the end. The list should have the following format: `"[[Order-description worked on by chef 0, Order-description worked on by chef 1, ...], ...]"`. An inner list at index `i` represents which order is being worked on by chef `i`. A list at index `j` describes the orders being executed at the `j-th` time step.

**Clarification:** The method should continue running until all orders are completed. Only after this can new orders be added again.

**Note:** Keep in mind that an order can only be executed once it has arrived. Please use the built-in list/array class of your language to return the results.

### Example

```java
restaurant = new Restaurant(2);

restaurant.addOrder(1, "Pommes", 5, 0, 3); // True, ["Pommes"]
restaurant.addOrder(2, "Salat", 5, 3, 2); // True, ["Pommes", "Salat"]
restaurant.addOrder(3, "Steak", 10, 0, 5); // True, ["Pommes", "Salat", "Steak"]
restaurant.addOrder(1, "Spaghetti", 10, 2, 7); // False
restaurant.addOrder(4, "Spaghetti", 10, 2, 7); // True, ["Pommes", "Salat", "Steak", "Spaghetti"]

restaurant.removeOrder(4); // True, ["Pommes", "Salat", "Steak"]

restaurant.getKMostUrgentOrders(2); // 3, "Steak", 10
                                    // 1, "Pommes", 5
                                    // 2, "Salat", 5

List<String[]> result = restaurant.execute();
// Output:
// [
//   ["Steak", "Pommes"],
//   ["Steak", "Pommes"],
//   ["Steak", "Pommes"],
//   ["Steak", "Salat"],
//   ["Steak", "Salat"]
// ]
```

---

# Task 5: CPU
### Task
Implement a Binary Search Tree that represents the CPU of a computer. Each process is represented as a node. Every process contains an `id` and a `category`.
Implement a class `Process`:

### `constructor(int id, String category)`
Which corresponds to the constructor of your chosen language and initializes the process ID with `id` and the category of the process with `category`.

### `int getID()`
Which returns the `id` of the process.

### `void setID(int id)`
Which sets the `id` of the process to the given `id`.

### `String getCategory()`
Which returns the `category` of the process.

### `void setCategory(String category)`
Which sets the `category` of the process to the given `category`.

### `getLeft()`
Which returns the left child of the process.

### `void setLeft(Process left)`
Which sets the left child of the process to the given process `left`.

### `getRight()`
Which returns the right child of the process.

### `void setRight(Process right)`
Which sets the right child of the process to the given process `right`.

Implement a class `Processor`:

### `constructor()`
Which corresponds to the constructor of your chosen language and creates an empty binary search tree.

### `Process getProcess(int id)`
Which returns the node with the given ID. If the ID is not in the tree, throw an `IndexOutOfBoundsException` in Java, or an `IndexError` exception in Python.

### `String getCategory(int id)`
Which returns the category of the process with the given ID. If the ID is not in the tree, throw an `IndexOutOfBoundsException` in Java, or an `IndexError` exception in Python.

### `void insert(int id, String category)`
Which adds a new process with the given parameters to the processor. If the ID is less than 0 or already in the tree, throw an `IndexOutOfBoundsException` in Java, or an `IndexError` exception in Python.

### `void delete(int id)`
Which deletes the process with the given ID. If the ID is less than 0 or not in the tree, throw an `IndexOutOfBoundsException` in Java.

### `getProcessesByCategory(String category)`
Which returns a list of all nodes of the processes that belong to the given category. If there are no processes in the given `category`, return an empty list.

### `getProcessesById(int lowerBound, int upperBound)`
Which returns a list of all processes that have an `id` greater than `lowerBound` and less than `upperBound`. The order of the list does not matter.

### `toInorderList()`
Which returns a list of nodes based on an in-order traversal of the tree.

### `leftView()`
Which returns a list containing the `id`s of the leftmost nodes at each level. The index of the value should correspond to the height of the node in the tree. The root is at the first index.

### `maxRootToLeafPath()`
Which returns the longest path from the root (starting point) to a leaf (ending point) in the tree.

### `height()`
Which returns the height of the processor. The root corresponds to height 0.

### `smallestGreaterKey(Process current, String category)`
This method finds the smallest process in the tree that is greater than the given process and belongs to the specified `category`. If no such process exists, return `null` or `None`.

### `findKthSmallest(int k)`
This method finds the k-th smallest process in the processor and returns it. If the k-th smallest process does not exist, the method should return `null` or `None`.

### `areIdentical(Processor otherProcessor)`
This method checks whether the given processor `otherProcessor` is identical to the current processor, meaning they have the same structure and all processes match. It returns `True` if the processors are identical, otherwise `False`.

### `getCommonAncestor(Process firstProcess, Process secondProcess)`
This method returns the common ancestor of the two processes. The common ancestor is the node from which both processes can be reached.

### `getLeafCount()`
This method returns the number of leaves in the tree, i.e., the number of nodes without children.

### `invert()`
Which inverts the processor so that smaller processes are stored on the right instead of the left. Newly added processes should also be stored on the right instead of the left. If `invert()` is called again, the processor structure and storage mode should be reversed again, so that smaller processes are once again stored on the left. Do not create new processes or a new processor structure while inverting.

### Example
```java
processor = new Processor();

processor.insert(10, "Game");
processor.insert(12, "Game");
processor.insert(11, "Application");
processor.insert(7, "Game");
processor.insert(8, "Game");
processor.insert(9, "Application");
processor.insert(17, "Application");
processor.insert(5, "Browser");

// Current Tree Structure:
//        10
//       /  \
//      7   12
//     / \   / \
//    5   8 11  17
//         \
//          9

processor.getNode(7);           // Output: [7, "Game"]

processor.getCategory(7);       // Output: "Game"

processor.getProcessesByCategory("Application");
// Output: [11, 9, 17]

processor.getProcessesById(9, 15);
// Output: [10, 12, 11]

processor.leftView();
// Output: [10, 7, 5, 9]

processor.toInorderList();
// Output: [5, 7, 8, 9, 10, 11, 12, 17]

processor.height();             // Output: 3

processor.remove(7);

// Updated Tree Structure:
//        10
//       /  \
//      5   12
//       \  / \
//        8 11 17
//         \
//          9
```

---

# Task 6: Graph
### Task

Implement an undirected graph. A graph is a tuple/list of vertices V and edges E: G=(V,E). Each vertex in the graph should have x and y coordinates within the integer range. An edge should be a bidirectional connection between two vertices. Implement the following methods to realize such a graph:

### `newNode(int x, int y)`
Which adds a new node to the graph and returns a unique number. This number should be represented by ascending numbers, starting from 0. Do not add the node if a node with the same x and y values already exists. In this case, return -1.

### `setEdge(int from, int to)`
Which creates an edge between the nodes from and to. Return `true` if the edge was successfully created, otherwise return `false`.

### `getEdges()`
Which returns a list of lists of nodes (integers). There should be one list of integers for each node. The i-th integer list should represent which nodes are reachable from node i.

### `getNGons(int n)`
Which takes an input parameter n and returns a list of lists of nodes. The method should find and store all pairwise disjoint n-Gons.
An n-Gon is a structure in the graph that is formed by starting at a node, reaching n-1 nodes through existing edges, and finally returning to the starting node. The nodes in the list should be arranged such that adjacent nodes in the list have an edge that was used for the n-Gon. The same applies to the pair formed by the first and last node in the list.

### `getLongestPath(int from, int to)`
Which returns a list of nodes (integers). The nodes should represent the nodes on the longest path from `from` to `to`. If no path exists, return an empty list. The length of the path is the sum of the individual edge lengths. Each node should only be visited once. The edge length between two points `(x1, y1)` and `(x2, y2)` is calculated as `(x1 - x2)^2 + (y1 - y2)^2`.

### `getNonCrossingGraph()`
Which returns a graph that has no crossing edges. To create this, generate a new graph from the calling graph, where intersection points of edges are replaced by a node located at the nearest coordinate. Remove the crossing edges from the graph and add new edges to the newly created node.

For example, given the points A(0,0), B(5,5), C(5,0), and D(0,5) with edges A-B and C-D, the edges intersect at point (2.5, 2.5). The nearest coordinate would be E(3,3). So, the new edges are A-E, B-E, C-E, and D-E. Round values at .5 up and round values below .5 down.

## Example

```java
     0
   / | \
  /  |  \
 3---|---1
  \  |  /
   \ | /
     2
TaskL_6 graph = new Task_6();
graph.newNode(0, 0); // 0
graph.newNode(5, 5); // 1
graph.newNode(5, 0); // 2
graph.newNode(0, 5); // 3

graph.setEdge(0, 1); // true
graph.setEdge(0, 1); // false
graph.setEdge(0, 0); // false
graph.setEdge(0, 2); // true
graph.setEdge(0, 3); // true
graph.setEdge(0, 4); // false
graph.setEdge(1, 3); // true
graph.setEdge(1, 2); // true
graph.setEdge(2, 3); // true

graph.getEdges();
// [
//   [1, 2, 3],
//   [0, 2, 3],
//   [0, 1, 3],
//   [0, 1, 2]
// ]

graph.getNGons(3);
// [
//   [0, 1, 3],
//   [0, 1, 2],
//   [0, 2, 3],
//   [1, 2, 3]
// ]

graph.getLongestPath(2, 1); // [2, 3, 0, 1]

graph.getNonCrossingGraph();
// Graph below

     1
   / | \
  /  |  \
 2---4---3
  \  |  /
   \ | /
     0
```
---

# Task 7: Energy Networks
### Task
A network operator wants to build a new energy infrastructure based on renewable energies. However, there are some uncertainties regarding the best infrastructure, distribution, and usage within the legal framework. The network operator has a rough 2D map of its area of interest. This area is given by a width and height. Furthermore, this area consists of grid squares. For each of these grid squares, there is various information available, such as the potential energy gain from wind turbines and solar panels. Additionally, for each grid square, it is specified whether it is populated. If it is populated, both the population and the total average energy consumption are given. Each square should also have a cost factor, which describes how expensive it would be to lay a cable over this square. The cost of a cable between two adjacent squares is described by adding the costs of both squares. Write a class `EnergyPlanner` that abstracts this problem in the form of a class. Implement the following methods:

### `constructor(int width, int height)`
Which corresponds to the constructor of your chosen language and creates a grid of size `width` x `height`. All fields should be uninhabited and have a potential energy gain of 0 for wind and solar energy.

### `setSettlement(int x, int y, int population, int powerConsumption)`
Which sets a settlement on the field `[x][y]` with a population of `population` and a total energy consumption of `powerConsumption`.

### `setEnergyPotential(int x, int y, String kind, int potential)`
Which sets the energy potential for the field `[x][y]` to `potential` for the energy type `kind`. `kind` can be either `solar` or `wind`.

### `setCost(int x, int y, int cost)`
Which sets the construction cost for laying a cable on the field `[x][y]`.

### `setWindTurbine(int x, int y)`
Which places a wind turbine on the field `[x][y]`, producing energy corresponding to the potential energy gain of the field.

### `setSolarPanel(int x, int y)`
Which places a solar panel on the field `[x][y]`, producing energy corresponding to the potential energy gain of the field.

### `getCost(int x1, int y1, int x2, int y2)`
Which returns the cable cost between the adjacent fields `[x1][y1]` and `[x2][y2]`.

### `getMinimalCostPath(int x1, int y1, int x2, int y2, float maxFlow)`
Which returns a potential path between `[x1][y1]` and `[x2][y2]`. The energy produced in `[x1][y1]` should be transmitted to `[x2][y2]`. The energy corresponds to the total energy produced by the wind and solar installations on the field, if any. Additionally, for each step of cable use, the transmitted energy is reduced by `0.1`. Find the cost-minimal path from `[x1][y1]` to `[x2][y2]` where energy still reaches the destination. Return this path as a list of lists of integers, where each inner list represents a coordinate pair, and the outer list represents the path from `[x1][y1]` to `[x2][y2]`. If there is no path where energy reaches the destination, return an empty list. The maximum energy flow through any cable section is limited to `maxFlow` units.

### `getMinimalCostCables(float maxFlow)`
Which returns a list of cable sections. Find a set of paths that cover as many settlements with electricity as possible in a cost-minimal way. The paths should be structured as in `getMinimalCostPath` and use `maxFlow` units of energy as the maximum flow per cable. If complete coverage is not possible, remove the settlements with the lowest population successively (while cables can still pass through these fields). Return a list of cable sections. Each cable section should be a list of strings. The first two entries represent the `[x][y]` coordinates of the origin, the third and fourth entries represent the `[x][y]` coordinates of the cable’s destination. The fifth entry should indicate how much energy was produced at the origin field and transmitted through the cable. The sixth entry should indicate how much energy is used at the destination field (consider the `0.1` energy loss per step). The seventh entry should represent how much energy is transmitted through this cable. The order of the cable sections does not matter.

### Example

```java
grid = EnergyPlanner(5, 3)

for i in range(5):
    for j in range(3):
        grid.setCost(i, j, 10)

grid.setCost(0, 2, 1)
grid.setCost(0, 1, 1)
grid.setCost(0, 0, 1)
grid.setCost(1, 0, 1)
grid.setCost(2, 0, 1)
grid.setCost(2, 1, 1)
grid.setCost(2, 2, 1)
grid.setCost(3, 2, 1)
grid.setCost(4, 2, 1)
grid.setCost(4, 1, 1)
grid.setCost(4, 0, 1)

// [01, 01, 01, 10, 01]
// [01, 10, 01, 10, 01]
// [01, 10, 01, 01, 01]

grid.setSettlement(4, 0, 10, 5)
grid.setSettlement(4, 2, 5, 3)

grid.setEnergyPotential(0, 2, "wind", 15)
grid.setEnergyPotential(0, 2, "solar", 2)

grid.setWindTurbine(0, 2)
grid.setSolarPanel(0, 2)

grid.getCost(0, 2, 1, 2)  # 11
grid.getCost(0, 2, 0, 1)  # 2

grid.getMinimalCostPath(0, 2, 4, 0, 30)
// Output:
// [
//    [0, 2], [0, 1], [0, 0], [1, 0], [2, 0],
//    [2, 1], [2, 2], [3, 2], [4, 2], [4, 1], [4, 0]
// ]

grid.getMinimalCostCables(30)
// Output:
// [
//    [0, 2, 0, 1, 16.0, 0.1, 16.0],
//    [0, 1, 0, 0, 0.0, 0.1, 15.9],
//    [0, 0, 1, 0, 0.0, 0.1, 15.8],
//    [1, 0, 2, 0, 0.0, 0.1, 15.7],
//    [2, 0, 2, 1, 0.0, 0.1, 15.6],
//    [2, 1, 2, 2, 0.0, 0.1, 15.5],
//    [2, 2, 3, 2, 0.0, 0.1, 15.4],
//    [3, 2, 4, 2, 0.0, 5.1, 15.3],
//    [4, 2, 4, 1, 0.0, 0.1, 10.1],
//    [4, 1, 4, 0, 0.0, 10.1, 10.1],
// ]
```

