import numpy as np

def north_west_corner(cost_matrix, supply, demand):
    # Initialize empty allocation matrix
    allocation = np.zeros(cost_matrix.shape)

    # Start from the top-left corner of the cost matrix
    i, j = 0, 0

    # Iterate until one of the supply or demand is exhausted
    while i < len(supply) and j < len(demand):
        # Calculate the possible allocation based on supply and demand
        quantity = min(supply[i], demand[j])

        # Update the allocation matrix
        allocation[i, j] = quantity

        # Update the supply and demand
        supply[i] -= quantity
        demand[j] -= quantity

        # Move to the next row or column
        if supply[i] == 0:
            i += 1
        else:
            j += 1

    return allocation

cost_matrix = np.array([[10, 20, 10],
                       [40, 60, 20],
                       [30, 40, 25]])

supply = [20, 50, 30]
demand = [30, 40, 35]

allocation_matrix = north_west_corner(cost_matrix, supply, demand)

print("Allocation Matrix:")
print(allocation_matrix)
