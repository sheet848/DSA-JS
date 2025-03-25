**Problem Statement:** 
Given an array representing a queue of customers and the value of bills they hold, determine if it is possible to provide correct change to each customer. Customers can only pay with 5$, 10$ or 20$ bills and we initially do not have any change at hand. Return true, if it is possible to provide correct change for each customer otherwise return false.

# Problem Statement

**Example 1:**
**Input:** 
bills = [5, 5, 5, 10, 20]
**Output:** True

**Explanation:** 
1. Initially we have 0 change and the queue of customers is [5, 5, 5, 10, 20].
2. First Customer pays 5$, no change required.
3. Second Customer pays 5$, no change required.
4. Third Customer pays 5$, no change required.
5. The Fourth Customer pays 10$, out of the three 5$ bills we have, we pay a 5$ bill and accept the 10$ bill.
6. Fifth Customer pays 20$, out of the two 5$ bills and one 10$ bill we have, we pay 15$ in change and have one 5$ bill left.

Hence, it is possible to provide change to all customers.

**Example 2:**
**Input:** 
bills = [5, 5, 10, 10, 20]
**Output:** False

**Explanation:** 
1. Initially, we have 0 change and the queue of customers is [5,5,10,10,20].
2. The first customer pays 5$, no change required.
3. The second customer pays 5$, no change required.
4. The third customer pays 10$, we collect a 5$ bill and give back a 5$ bill.
5. The fourth customer pays 10$, we collect a 5$ bill and give back a 5$ bill.
6. The fifth customer pays 20$, we cannot give the change of $15 back because we only have two $10 bills.
7. Since not every customer received the correct change, the answer is false.

# Solution

```Javascript

                            
// Function to find whether each customer can 
// be provided with correct change
function lemonadeChange(bills) {
    
    // Initialize a counter
    // for $5 bills
    let five = 0; 
    
    // Initialize a counter
    // for $10 bills
    let ten = 0;   
    
    // Iterate through each customer's bill
    for(let i = 0; i < bills.length; i++){
        
        // If the customer's
        // bill is $5
        if(bills[i] === 5){
            
            // Increment the
            // count of $5 bills
            five++;  
        }
        
        // If the customer's
        // bill is $10
        else if(bills[i] === 10){
            
            // Check if there are $5
            // bills available to give change
            if(five){
                 // Use one $5 bill
                 // to give change
                five--; 
                // Receive one $10 bill
                ten++;   
            }
            
            // If no $5 bill
            // available, return false
            else return false;  
        }
        
        // If the customer's
        // bill is $20
        else {
            // Check if there are both
            // $5 and $10 bills
            // available to give change
            if(five && ten){
                 // Use one $5 bill
                five--; 
                // Use one $10 bill
                ten--;   
            }
            // If there are not enough $10 bills,
            // check if there are at least
            // three $5 bills available
            else if (five >= 3){
                // Use three $5 bills
                // to give change
                five -= 3;  
            }
            // If unable to give
            // change, return false
            else return false;  
        }
    }
    
    // Return true if all customers
    // are served with correct change
    return true;  
}


let bills = [5, 5, 5, 10, 20];
console.log("Queues of customers: " + bills.join(" "));
let ans = lemonadeChange(bills);
if(ans)
    console.log("It is possible to provide change for all customers.");
else
    console.log("It is not possible to provide change for all customers.");
                            
                        
```

**Time Complexity: O(N)** where N is the number of people in queue/ bills we will deal with. We iterate through each customer’s bills exactly once. The loop runs for N iterations and at each iteration the operations performed are constant time.

**Space Complexity: O(1)** as the algorithm uses only a constant amount of extra space regardless of the size of the input array. It does not require any additional data structures that scale with the input size.