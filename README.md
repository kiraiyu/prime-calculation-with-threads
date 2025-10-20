# Assignment 3 - Prime Calculation with Threads
This project leverages multithreading for concurrent prime number calculation, allowing for faster computation on multi-core systems.

# Data input with command-line argument:
The program should accept a single command-line argument: an integer limit, which specifies the upper bound for prime number calculation. Example: If the user runs the program with the input 50, the program should output all prime numbers from 1 to 50. Example usage: ./prime_numbers 50 
See code sample https://www.geeksforgeeks.org/command-line-arguments-in-cpp/ (Links to an external site). 

# Thread Creation:
The program must create multiple threads to divide the prime number calculation.
The number of threads should be determined by std::thread::hardware_concurrency(), which detects the number of available hardware threads on the system. See code sample below.
Each thread will process a specific range of numbers to check for primes.

# Prime Calculation:
Each thread will independently calculate primes within its assigned range.
The prime checking function should efficiently determine if a number is prime.

# Thread Range Assignment:
The range for each thread is determined by dividing the limit by the number of threads (numThreads).
Example: For limit = 50 and numThreads = 4, thread 1 will handle numbers from 1 to 12, thread 2 from 13 to 24, thread 3 from 25 to 36, and thread 4 from 37 to 50.
The last thread should handle any remaining numbers if the limit does not divide evenly by the number of threads.
Per-Thread Result Storage and Delayed Merge
Each thread stores its prime numbers in a local vector.
Each thread writes its results to a separate temporary file, e.g., primes_thread_X.txt (X = thread number).
After all threads finish, the main thread reads all temporary files, merges the numbers into a single vector, sorts it, and outputs the final prime list.
Example:

Thread 1 writes 2 3 5 7 11 13 → primes_thread_1.txt
Thread 2 writes 17 19 23 29 → primes_thread_2.txt
Thread 3 writes 31 37 41 → primes_thread_3.txt
Thread 4 writes 43 47 → primes_thread_4.txt
Main thread merges → final sorted output:

Prime numbers less than or equal to 50: 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47

Final output: the sorted list of prime numbers in ascending order.

# Additional Considerations: Ensure the program runs efficiently. Comment and document the code for clarity and maintainability. Test the program with various input cases to ensure correctness.

Deliverable: A C++ code that implements the coding requirements. Provide the source code by copying and pasting it directly (avoid using screenshots of the code), and include screenshots displaying the output from at least 3 different test cases. Use your creativity and think about different test cases. 
