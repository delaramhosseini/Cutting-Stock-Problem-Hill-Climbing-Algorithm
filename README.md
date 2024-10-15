# Hill Climbing Algorithm for Cutting Stock Optimization

This project implements the **Hill Climbing Algorithm** to solve the **Cutting Stock Problem**, where the goal is to minimize waste when cutting large rolls of material into smaller pieces to meet customer demands. The algorithm iteratively improves a solution by exploring neighboring solutions and selecting the one that uses the fewest rolls.

## Introduction

The **Hill Climbing Algorithm** is a local search optimization technique used to find the best possible solution for a given problem by incrementally improving an initial solution. In this project, it is applied to find an efficient cutting pattern for rolls of material to meet customer requests while minimizing waste.

## Hill Climbing Algorithm Overview

The **Hill Climbing Algorithm** is a local search optimization technique that starts with an initial solution and iteratively improves it by exploring neighboring solutions. The algorithm works by moving to the best neighboring solution (the one that improves the current state the most) and repeating the process until no better neighbors are found or a stopping condition is met.

### Key Characteristics of Hill Climbing:
- **Local Search**: Hill Climbing only explores neighboring solutions, meaning it can get stuck in local optima (suboptimal solutions that are better than surrounding solutions but not globally optimal).
- **Greedy Approach**: It always chooses the best solution from the current set of neighbors, making it a greedy algorithm.
- **Simple to Implement**: The algorithm is easy to implement and can quickly find reasonable solutions for many optimization problems.

### Advantages:
- **Efficiency**: It can find good solutions quickly in many practical problems.
- **Simplicity**: The algorithm is easy to understand and implement, making it a popular choice for basic optimization tasks.

### Limitations:
- **Local Optima**: Since the algorithm only considers local neighbors, it can get stuck in suboptimal solutions without finding the global optimum.
- **No Backtracking**: Once a solution is accepted, the algorithm doesn't explore previous solutions, which may lead to missing better alternatives.

## Project Structure

1. **Class Initialization** (`Hill_Climbing_Algorithm`):
   - The class is initialized with several instance variables:
     - `number_of_requests`: The number of requests for smaller pieces.
     - `list_of_requests`: The specific sizes requested by customers.
     - `length_of_roll`: The length of each available roll.
     - `current_answer`: Represents the current cutting pattern (solution).
     - `current_fitness`: The number of rolls currently used.
     - `neighbors`: A list of possible neighboring solutions (alternative cutting patterns).
     - `expected_number_of_rolls`: The ideal number of rolls needed to minimize waste.
     - `maximum_iterations`: The maximum number of iterations for the algorithm.

2. **Input Function** (`input`):
   - This function reads data from a file containing:
     - The length of a roll.
     - A list of customer requests for specific sizes.
     - The expected number of rolls to use.
   - The data is stored in instance variables for further use in the algorithm.

3. **Initialization Function** (`initialize`):
   - This function sets up the instance variables based on the input data, including:
     - Initializing the list of requests, the roll length, and the number of requests.
     - Generating the `current_answer` (an initial cutting pattern).
     - Calculating the `current_fitness` using the `fitness_function`.

4. **Initial Index of Request** (`initial_index_of_request`):
   - This function generates an initial cutting pattern by selecting indexes from the beginning and end of the request list. If the number of requests is odd, it excludes the last index.

5. **Fitness Function** (`fitness_function`):
   - This function calculates the fitness of a proposed cutting pattern (solution) by:
     - Iterating through the requests in the cutting.
     - Tracking the total number of rolls used.
     - Incrementing the roll counter whenever the sum of pieces exceeds the roll length.
   - The function returns the total number of rolls used as the fitness value.

6. **Create Neighbors Function** (`create_neighbours`):
   - This function generates neighboring cutting patterns by:
     - Making a deep copy of the `current_answer`.
     - Swapping random elements within the copy to create new cutting patterns.
     - Adding the new patterns to the `neighbors` list.

7. **Get Best Neighbor Function** (`get_best_neighbour`):
   - This function evaluates all neighboring cutting patterns by sorting them based on their fitness values (number of rolls used).
   - It returns the best neighbor, i.e., the one that uses the fewest rolls.

8. **Run Function** (`run`):
   - The core of the algorithm that iteratively:
     - Creates new neighbors.
     - Selects the best neighbor from the list.
     - Updates the `current_answer` if the fitness of the best neighbor is better than the current fitness.
     - Continues the process until the maximum number of iterations is reached or the fitness of the current solution matches or exceeds the expected number of rolls.
