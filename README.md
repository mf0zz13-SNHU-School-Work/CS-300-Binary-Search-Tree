# Bid Management with a Binary Search Tree

**Status:** Supporting CS-300 lab. This is a Windows/Visual Studio C++ learning project, not a production bid-management system.

The program loads bid records from a course-provided CSV file and stores them in a custom, unbalanced binary search tree keyed by bid ID. Its console menu supports loading data, displaying records in key order, finding one bid, and removing a bid.

## Implemented behavior

- Models each bid with an ID, title, fund, and amount.
- Inserts and searches by bid ID.
- Implements in-order, pre-order, and post-order traversal; the menu uses in-order traversal to display bids in sorted key order.
- Handles removal for leaf nodes, one-child nodes, and two-child nodes inside the recursive helper.
- Measures CSV-load and lookup time with the C runtime clock.
- Accepts an optional CSV path and lookup ID as command-line arguments.

## Complexity

The tree is not self-balancing, so runtime depends on its height, h.

| Operation | Cost |
| --- | --- |
| Insert | O(h) |
| Search | O(h) |
| Remove | O(h) |
| Full traversal | O(n) |

For a reasonably balanced tree, height is approximately O(log n). Ordered input can create a skewed tree with O(n) insert, search, and removal behavior.

## Repository layout

- [BinarySearchTree.cpp](./BinarySearchTree/BinarySearchTree.cpp) — tree implementation, CSV loading, and console menu
- [CSVparser.cpp](./BinarySearchTree/CSVparser.cpp) and [CSVparser.hpp](./BinarySearchTree/CSVparser.hpp) — course CSV-parser support
- [eBid_Monthly_Sales.csv](./BinarySearchTree/eBid_Monthly_Sales.csv) — sample input
- [BinarySearchTree.sln](./BinarySearchTree/BinarySearchTree.sln) — Visual Studio solution

## Build and run

The committed project targets the Visual Studio v143 toolset and Windows 10 SDK.

1. Install Visual Studio 2022 with the **Desktop development with C++** workload.
2. Open [BinarySearchTree.sln](./BinarySearchTree/BinarySearchTree.sln).
3. Build the x64 Debug configuration.
4. Run with the working directory set to the folder containing the CSV file, or pass the CSV path and optional bid ID to the executable.

The default lookup ID is `98223`. The source and project configuration were reviewed for this documentation update; no fresh compile or runtime result is claimed.

## Known limitations

- There is no automated test suite.
- The tree does not rebalance itself.
- CSV parsing and numeric conversion assume the supplied dataset's format.
- The public `Remove` wrapper discards the root returned by the recursive helper. Removing the current root can therefore leave an invalid root pointer and should be corrected before this code is reused.
- Generated Visual Studio files and build outputs are currently tracked in the repository.

## Academic context

This repository contains work completed for SNHU CS-300. The source identifies Michael Foster as the author and SNHU COCE as the copyright holder. It includes course project structure, a CSV parser, and supplied data; it should be evaluated as a data-structure exercise rather than a standalone application.

See the [canonical CS-300 course planner and reflection](https://github.com/mf0zz13-SNHU-School-Work/CS-300-Reflection) for the course's final project and data-structure analysis.
