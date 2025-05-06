# B-Tree Implementation in C++

## Overview
This project implements a B-Tree data structure in C++ to efficiently manage a collection of keys with operations like insertion and traversal. While initially intended as a B+ Tree for a Classroom Booking System (as referenced in prior discussions), this implementation is a standard B-Tree, which can still be adapted for managing booking records. A B-Tree is a self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations, making it suitable for systems requiring fast access to large datasets, such as a classroom booking system.

## Features
- **Insert Keys**: Add new keys to the B-Tree while maintaining its balanced properties.
- **Level-Order Traversal**: Print the tree in a level-order format with proper indentation to visualize its structure.
- **Balanced Structure**: Ensures the tree remains balanced with a minimum degree `t = 3`, allowing up to `2t-1` keys per node.
- **Scalable Design**: Supports efficient operations with a time complexity of O(log n) for insertion and search.

## Why B-Tree?
A B-Tree is ideal for systems that need to handle large datasets with frequent insertions and searches, such as a classroom booking system. It provides:
- Logarithmic time complexity (O(log n)) for key operations.
- High fan-out (many children per node), reducing tree height and minimizing disk I/O in disk-based systems.
- Balanced structure, ensuring consistent performance even as the dataset grows.

However, this implementation is a B-Tree, not a B+ Tree as initially intended for the Classroom Booking System. A B+ Tree would store all data in leaf nodes with linked leaves for efficient range queries, which is more suitable for booking systems (e.g., retrieving all bookings for a date). This B-Tree implementation stores data in both internal and leaf nodes, which is less optimal for range queries but still functional for key-based lookups.

## Code Structure
- **BTreeNode Class**:
  - `keys`: A vector to store the node's keys (up to `2t-1` keys).
  - `children`: A vector of pointers to child nodes (up to `2t` children).
  - `isLeaf`: Boolean indicating if the node is a leaf.
  - `numKeys`: Number of keys currently in the node.
- **BTree Class**:
  - `root`: Pointer to the root node of the tree.
  - `insert(key)`: Inserts a new key into the tree, handling node splitting if necessary.
  - `splitChild(parent, i)`: Splits a full child node during insertion.
  - `insertNonFull(node, key)`: Inserts a key into a non-full node recursively.
  - `printTree(node, depth)`: Prints the tree in level-order with indentation for visualization.
  - `print()`: Wrapper to call `printTree` starting from the root.

## Installation
Follow these steps to set up and run the project on your local machine.

### Prerequisites
- A C++ compiler (e.g., g++ for GCC, MSVC for Visual Studio)
- Git (to clone the repository)

### Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/btree-implementation.git
   cd btree-implementation
   ```

2. **Compile the Code**:
   - Using g++:
     ```bash
     g++ -o btree main.cpp
     ```
   - Using another compiler (e.g., Visual Studio), open the project and build it.

3. **Run the Program**:
   ```bash
   ./btree
   ```
   The program will insert a few sample keys (10, 20, 5, 6, 12, 30) and print the resulting B-Tree structure.

## Usage
- The `main()` function demonstrates the B-Tree by inserting keys and printing the tree.
- Sample output for the given keys (10, 20, 5, 6, 12, 30):
  ```
  B-tree structure:
  10 20
      5 6
      12
      30
  ```
  - The root node contains keys `10` and `20`.
  - Its children (at depth 1) are:
    - Node with keys `5` and `6`.
    - Node with key `12`.
    - Node with key `30`.

- To modify the keys, edit the `main()` function to call `btree.insert()` with different values.
- To integrate with a Classroom Booking System, modify the B-Tree to store booking records (e.g., a composite key of `(classroom_id, date, start_time)` and associated data).

## Adapting for Classroom Booking System
This B-Tree implementation can be adapted for your Classroom Booking System by:
1. **Switching to a B+ Tree**:
   - Modify the structure to store all data in leaf nodes.
   - Link leaf nodes for efficient range queries (e.g., retrieving all bookings for a date).
   - Update `insert` and `print` methods accordingly.
2. **Storing Booking Records**:
   - Replace the `int` keys with a composite key structure (e.g., a struct with `classroom_id`, `date`, and `start_time`).
   - Store additional data (e.g., user name, end time) in leaf nodes.
3. **Adding Operations**:
   - Implement a `search` method to check for booking conflicts.
   - Add a `delete` method to cancel bookings.
   - Use range queries to display all bookings for a classroom or date.

## Known Issues
- **Not a B+ Tree**: The implementation is a B-Tree, not a B+ Tree, which was the intended structure for the Classroom Booking System. B+ Trees are more suitable for range queries due to linked leaf nodes.
- **No Deletion**: The code lacks a method to delete keys, which is necessary for canceling bookings.
- **Basic Visualization**: The level-order print function provides a simple visualization but could be enhanced for better readability.

## Future Improvements
- Convert the implementation to a B+ Tree by storing data only in leaf nodes and linking them.
- Add a `delete` method to support canceling bookings.
- Implement a `search` method to check for booking conflicts.
- Enhance the `print` function to include more details (e.g., tree height, node types).
- Integrate with a user interface (e.g., Tkinter, as in your Billing System) for easier interaction.
- Add persistence to save the tree to disk, similar to the bill-saving functionality in your Billing System.

## License
MIT License
