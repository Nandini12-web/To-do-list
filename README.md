# To-do-list
class Task:
    def __init__(self, description, completed=False):
        self.description = description
        self.completed = completed

    def __str__(self):
        status = "[X]" if self.completed else "[ ]"
        return f"{status} {self.description}"

class TodoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, description):
        task = Task(description)
        self.tasks.append(task)
        print(f"Task '{description}' added.")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in your To-Do list.")
            return
        print("\nYour To-Do List")
        for i, task in enumerate(self.tasks):
            print(f"{i + 1}. {task}")
        print("---------------\n")

    def complete_task(self, task_number):
        if 0 < task_number <= len(self.tasks):
            self.tasks[task_number - 1].completed = True
            print(f"Task {task_number} marked as completed.")
        else:
            print("Invalid task number.")

    def delete_task(self, task_number):
        if 0 < task_number <= len(self.tasks):
            removed_task = self.tasks.pop(task_number - 1)
            print(f"Task '{removed_task.description}' deleted.")
        else:
            print("Invalid task number.")

def main():
    todo_list = TodoList()

    while True:
        print("To-Do List Application")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Complete")
        print("4. Delete Task")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            description = input("Enter task description: ")
            todo_list.add_task(description)
        elif choice == '2':
            todo_list.view_tasks()
        elif choice == '3':
            try:
                task_num = int(input("Enter task number to mark as complete: "))
                todo_list.complete_task(task_num)
            except ValueError:
                print("Invalid input. Please enter a number.")
        elif choice == '4':
            try:
                task_num = int(input("Enter task number to delete: "))
                todo_list.delete_task(task_num)
            except ValueError:
                print("Invalid input. Please enter a number.")
        elif choice == '5':
            print("Exiting To-Do List Application. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
