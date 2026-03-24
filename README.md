# todo-list
## Description
The To-Do List Application is a simple yet practical task management system developed using Python. It allows users to create, manage, and track daily tasks efficiently through a command-line interface (CLI).

This project demonstrates how basic programming concepts can be used to solve real-world productivity problems such as organizing daily activities and tracking progress.

## Objective
The main objectives of this project are:

To help users manage their daily tasks efficiently
To understand file handling in Python
To implement CRUD operations (Create, Read, Update, Delete)
To build a real-time usable application using basic Python
To Understand Modular Programming
Break the program into smaller functions like:
add_task()
view_tasks()
delete_task()
Improves code readability and maintenance
Helps in reusing code efficiently

The objective of this project is not only to manage daily tasks but also to understand key programming concepts such as modular programming, file handling, error handling, data structures, and CRUD operations. It also aims to improve logical thinking, debugging skills, and provide a foundation for developing advanced real-world applications.

## Features

Task Management
Add new tasks
View all tasks
Mark tasks as completed
Delete tasks
💾 Data Persistence
Tasks are saved in a file (tasks.json)
Data remains even after closing the program
⚠️ Error Handling
Handles invalid inputs
Prevents crashes during wrong operations
📊 Status Tracking
Each task shows:
✔ Completed
✘ Not completed

## Technologies Used

Programming Language: Python
Libraries Used:
json → for storing data
os → for file handling
Interface: Command Line Interface (CLI)

## System Architecture

The application follows a simple modular structure:

Main Module
Displays menu
Takes user input
Task Module
Add task
View tasks
Delete task
Mark task as done
File Handling Module
Load tasks from file
Save tasks to file

## python program 

```
import json
import os

FILE_NAME = "tasks.json"

# Load tasks from file
def load_tasks():
    if os.path.exists(FILE_NAME):
        with open(FILE_NAME, "r") as file:
            return json.load(file)
    return []

# Save tasks to file
def save_tasks(tasks):
    with open(FILE_NAME, "w") as file:
        json.dump(tasks, file)

# Add a new task
def add_task(tasks):
    task = input("Enter new task: ")
    tasks.append({"task": task, "done": False})
    save_tasks(tasks)
    print("Task added!")

# View tasks
def view_tasks(tasks):
    if not tasks:
        print("No tasks available.")
        return

    print("\nYour Tasks:")
    for i, t in enumerate(tasks):
        status = "✔" if t["done"] else "✘"
        print(f"{i+1}. {t['task']} [{status}]")

# Mark task as completed
def mark_done(tasks):
    view_tasks(tasks)
    try:
        num = int(input("Enter task number to mark done: "))
        tasks[num-1]["done"] = True
        save_tasks(tasks)
        print("Task marked as completed!")
    except:
        print("Invalid input!")

# Delete task
def delete_task(tasks):
    view_tasks(tasks)
    try:
        num = int(input("Enter task number to delete: "))
        removed = tasks.pop(num-1)
        save_tasks(tasks)
        print(f"Deleted task: {removed['task']}")
    except:
        print("Invalid input!")

# Main menu
def main():
    tasks = load_tasks()

    while True:
        print("\n==== TO-DO LIST ====")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task Done")
        print("4. Delete Task")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            add_task(tasks)
        elif choice == "2":
            view_tasks(tasks)
        elif choice == "3":
            mark_done(tasks)
        elif choice == "4":
            delete_task(tasks)
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid choice!")

# Run program
if __name__ == "__main__":
    main()
```
<img width="1227" height="957" alt="image" src="https://github.com/user-attachments/assets/9f0b32a2-ffeb-4ae4-afc4-599e81ebda6c" />
<img width="1132" height="869" alt="image" src="https://github.com/user-attachments/assets/39f04387-eadd-4261-b018-95ba468f2b60" />


## Sample Execution
```
==== TO-DO LIST ====
1. Add Task
2. View Tasks
3. Mark Task Done
4. Delete Task
5. Exit
Enter your choice: 1

Enter new task: Study Python
Task added!

Enter your choice: 2

Your Tasks:
1. Study Python [✘]

Enter your choice: 3
Enter task number to mark done: 1

Your Tasks:
1. Study Python [✔]
```

## Output

<img width="542" height="864" alt="image" src="https://github.com/user-attachments/assets/35921fe1-ed67-478a-9860-f048914245a9" />

<img width="584" height="888" alt="image" src="https://github.com/user-attachments/assets/3eb23d44-52ed-4bff-81d8-d28175e86ae6" />





## Working Process

When the program starts:
It checks if tasks.json exists
Loads existing tasks

User is shown a menu:
```
1. Add Task
2. View Tasks
3. Mark Task Done
4. Delete Task
5. Exit
```
Based on user input:

Task is added / updated / deleted
After every operation:
Data is saved automatically
Program continues until user exits
## Data Structure
```
[
  {"task": "Study Python", "done": false},
  {"task": "Complete project", "done": true}
]
```
## Testing

The application was tested for:

Adding multiple tasks
Deleting tasks
Handling invalid inputs
File creation and data persistence

## Advantages

Simple and easy to use
Beginner-friendly project
Helps improve productivity
Demonstrates real-world application of Python

## Limitations

No graphical user interface (GUI)
Limited to local storage (JSON file)
No reminders or notifications

## Future enhancements

Add GUI using tkinter
Add deadline & reminders
Store data in database (SQLite/MySQL)
Convert into web app using Flask/Django
Add user authentication system

## Conclusion

The To-Do List Application is a fundamental Python project that helps in understanding core programming concepts like file handling, data structures, and user interaction. It serves as a strong foundation for building more advanced real-time applications.


