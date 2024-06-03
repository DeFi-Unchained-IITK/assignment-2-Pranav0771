# Assignment-2

## Solution 1 :
#### PrimeOwner Contract
The PrimeOwner contract is a simple Ethereum smart contract written in Solidity. Its primary purpose is to allow ownership transfer based on a certain condition - in this case, determining whether a given number is a prime number.
#### Functioning
##### Constructor
The constructor initializes the contract, setting the deploying address as the initial owner.

##### work(uint num)
This function takes a single parameter, num, representing the number to be processed. If num is a prime number, ownership of the contract is transferred to the caller of the function. There is also a condition that num>=1, if num doesn't satisfy this condition then revert the function.(below is an example)

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/c6a71584-5eee-4a95-aa0c-0d1b2d430a6d)

Also an example if num is not prime.(No change of owner)

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/66610a02-19d8-4a8c-88ca-74208991651e)

##### isPrime(uint _num)
This function checks whether a given number _num is prime. It returns true if the number is prime, and false otherwise.

##### Events(ownerChange)
This event is emitted whenever ownership of the contract changes. It logs the previous owner's address and the new owner's address.<br />
An example of a successful owner change:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/7e7ef390-27fe-45a1-baf5-a5b8c82736f2)


## Solution 2 :

#### EmployeeRegistree Contract
The EmployeeRegistree contract is a simple Ethereum smart contract designed to manage employee records. It allows for the addition, updating, retrieval, and deletion of employee information.

#### Functioning
##### Events
We have defined three events, which are:<br />
newEmployeeAdded: This event is emitted when a new employee is added to the registree. It logs the ID, name, position, and salary of the new employee.<br />
EmployeeUpdated: This event is emitted when an employee's details are updated. It logs the ID, name, position, and salary of the updated employee.<br />
EmployeeDeleted: This event is emitted when an employee is deleted from the registree. It logs the ID, name, position, and salary of the deleted employee.

##### state variable employee_id
This helps to assign IDs to new employees.

##### AddEmployee(string memory name, string memory position, uint salary)
This function adds a new employee to the registree. It takes the employee's name, position and salary as parameters.

![Screenshot 2024-06-03 181800](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/6ff0cccb-c88a-41de-8ad3-359e1c79a6e5)

##### GetEmployeeDetails(uint id)
This function retrieves the details of an employee by providing their id. First checks if the id is valid(by checking if book struct isn't empty for the id and id is less than employee_id) then returns the name, position, and salary of the employee. If id is invalid the function is reverted.

![Screenshot 2024-06-03 181944](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/52748e74-3296-4544-96a2-250f310d9382)

For Invalid id case:

![Screenshot 2024-06-03 183805](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/c19ad498-4ccd-4bb9-8657-67b500884e6c)


##### UpdateEmployee(uint id, string memory name, string memory position, uint salary)
This function updates the details of an existing employee. It takes the employee's ID and the updated name, position, and salary as parameters. Also checks if the id is valid(by checking if book struct isn't empty for the id and id is less than employee_id) or not. If id is invalid the function is reverted.

![Screenshot 2024-06-03 182159](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/fe206767-82a1-4296-bc03-215b156cd94f)

For Invalid id case:

![Screenshot 2024-06-03 184034](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/09175daf-48d8-478d-93fa-d26e995ff36b)


##### DeleteEmployee(uint id)
This function deletes an employee from the registry based on their id after checking if the id is valid(by checking if book struct isn't empty for the id and id is less than employee_id). If id is invalid the function is reverted.

![Screenshot 2024-06-03 182230](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/d1dd73e9-feee-4cff-8805-4ab080919dc0)

For Invalid id case:

![Screenshot 2024-06-03 184111](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/4669664a-86ad-4abe-a75c-8b5306f2ffb5)


## Solution 3 :

#### Library Contract
The Library contract is an Ethereum smart contract designed to manage a library system. It allows for the addition of books, borrowing, and returning of books by users.
#### Functioning
##### Mapping
We have defined two maps here. First one is books, which maps ID of the book to its details, which is helpful in finding the books by their unique IDs. Second one borrowed_books, which maps the address of the borrower to the Book. We have taken an array of books to tackle the case when a borrower borrows two or more books.

##### Modifier validID(uint id)
We have defined a modifier validID to check if the id given as parameter to a function is valid or not.

##### AddBook(string memory name, string memory author)
This function is used to add a new book to the library. It takes the name and author of the book as parameters and assigns a unique ID to the book and adds it to the books mapping and making the availability as true.<br />
OUTPUT:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/ad1e1a65-f819-474a-9add-e7a1c4cb5950)

##### BorrowBook(uint id)
Users can borrow a book by calling this function with the ID of the book they want to borrow. If id is invalid the function is reverted. The function checks if the book is available and adds it to the borrower's list of borrowed books by using the push operator and marking the avilability as false. <br />
OUTPUT:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/1c1eb281-e876-44c1-ae31-675e7921e4f4)

For Invalid id case:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/d4e62000-b00b-46f8-9c3d-58602335ff3f)

##### GetBookDetails(uint id)
This function allows users to retrieve details of a book by providing its ID. It returns the name, author and availability status of the book. If id is invalid the function is reverted.

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/f265de01-f7e8-4eca-a797-5c3c952a8ae7)

For Invalid id case:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/2726c253-979d-47dd-9169-5d7a89ef4d22)

##### ReturnBook(uint id)
Users can return a book they have borrowed by calling this function with the ID of the book. If id is invalid the function is reverted. The function checks if the caller has borrowed any books or not, if not then function is reverted with reason that No book borrowed by caller. If the functions finds a book having the input id with the address of owner, the function removes the book from the borrower's list of borrowed books and updates the availability status of the book. We have first swapped the book that is to be removed from borrowed books list with the last book in the array of books borrowed by caller and then using pop operator to remove it from the list. This is done so that system doesn't have to work extra to check if the id matches with one in the list because if we didn't swapped and used delete instead then the push operator would add newly borrowed books continuing the past indexes. If no book with required id in the address of the borrower, function is reverted with reason Book not borrowed by the caller.<br />
OUTPUT:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/9a00b305-2c22-44f4-9c86-ba417f8f48a8)

For Invalid Id case:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/c5ad0fb8-cc30-4647-9478-8ca6905b788c)

Incase the book with id as parameter isn't borrowed by caller:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/1ae1bbd2-a18d-43ea-9bc1-cb41b9b14922)

Incase no book borrowed by caller:

![image](https://github.com/DeFi-Unchained-IITK/assignment-2-Pranav0771/assets/169836989/d53f209f-27f2-48e3-b353-8d018b752d80)















