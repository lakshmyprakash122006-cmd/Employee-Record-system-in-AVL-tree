# Employee-Record-system-in-AVL-tree
Data structure practical program 
# Employee ID Management using AVL Tree

class Node:
    def __init__(self, emp_id):
        self.emp_id = emp_id
        self.left = None
        self.right = None

def insert(root, emp_id):
    if root is None:
        return Node(emp_id)

    if emp_id < root.emp_id:
        root.left = insert(root.left, emp_id)
    else:
        root.right = insert(root.right, emp_id)

    return root

def delete(root, emp_id):
    if root is None:
        return root

    if emp_id < root.emp_id:
        root.left = delete(root.left, emp_id)
    elif emp_id > root.emp_id:
        root.right = delete(root.right, emp_id)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left

        temp = root.right
        while temp.left:
            temp = temp.left

        root.emp_id = temp.emp_id
        root.right = delete(root.right, temp.emp_id)

    return root

def display(root):
    if root:
        display(root.left)
        print("Employee ID:", root.emp_id)
        display(root.right)

root = None

while True:
    print("\n1.Add Employee")
    print("2.Delete Employee")
    print("3.Display Employees")
    print("4.Exit")

    ch = int(input("Enter choice: "))

    if ch == 1:
        eid = int(input("Enter employee ID: "))
        root = insert(root, eid)

    elif ch == 2:
        eid = int(input("Enter employee ID to delete: "))
        root = delete(root, eid)

    elif ch == 3:
        display(root)

    elif ch == 4:
        break
output:
1.Add Employee
2.Delete Employee
3.Display Employees
4.Exit

Enter choice: 1
Enter employee ID: 101

Enter choice: 1
Enter employee ID: 105

Enter choice: 3
Employee ID: 101
Employee ID: 105

Enter choice: 2
Enter employee ID to delete: 101
