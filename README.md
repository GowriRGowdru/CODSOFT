# CODSOFT
 This repository contains Python projects for the internship

## Tasks:

# A Simple To-Do List Application
 tasks = []  # List to store tasks

 def add_new_task(task_name):
    """Adds a new task to the list"""
    tasks.append({'name': task_name, 'completed': False})

 def show_all_tasks():
    """Displays all tasks in the list"""
    if len(tasks) == 0:
        print("No tasks added yet!")
        return
    
    print("\nYour To-Do List:")
    for i, t in enumerate(tasks):
        status = "✔ Done" if t['completed'] else "✗ Pending"
        print(f"{i + 1}. {t['name']} - {status}")

 def complete_task(task_index):
    """Marks a task as completed"""
    if task_index >= 0 and task_index < len(tasks):
        tasks[task_index]['completed'] = True
        print("Task marked as completed!")
    else:
        print("Invalid task number. Please try again.")

 def remove_task(task_index):
    """Removes a task from the list"""
    if task_index >= 0 and task_index < len(tasks):
        deleted_task = tasks.pop(task_index)
        print(f"Deleted task: {deleted_task['name']}")
    else:
        print("Invalid task number. Please try again.")

 if __name__ == "__main__":
    print("Welcome to the To-Do List Manager!")
    
    while True:
        print("\nOptions:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Completed")
        print("4. Delete Task")
        print("5. Exit")
        
        try:
            choice = int(input("Select an option (1-5): "))
            if choice == 1:
                task_input = input("Enter the task description: ")
                add_new_task(task_input)
                print("Task added successfully!")
            elif choice == 2:
                show_all_tasks()
            elif choice == 3:
                show_all_tasks()
                task_num = int(input("Enter the task number to complete: ")) - 1
                complete_task(task_num)
            elif choice == 4:
                show_all_tasks()
                task_num = int(input("Enter the task number to delete: ")) - 1
                remove_task(task_num)
            elif choice == 5:
                print("Thanks for using To-Do List Manager! Goodbye.")
                break
            else:
                print("Invalid choice. Please enter a number between 1 and 5.")
        except ValueError:
            print("Invalid input. Please enter a valid number.")



# Simple Calculator
def calculator():
    while True:
        try:
            num1 = float(input("Enter the first number: "))
            num2 = float(input("Enter the second number: "))
            print("Operations: +, -, *, /")
            operation = input("Choose an operation: ")
            if operation == '+':
                print(f"Result: {num1 + num2}")
            elif operation == '-':
                print(f"Result: {num1 - num2}")
            elif operation == '*':
                print(f"Result: {num1 * num2}")
            elif operation == '/':
                if num2 == 0:
                    print("Error: Division by zero!")
                else:
                    print(f"Result: {num1 / num2}")
            else:
                print("Invalid operation!")
        except ValueError:
            print("Invalid input! Please enter numbers only.")

        again = input("Perform another calculation? (yes/no): ").lower()
        if again != 'yes':
            print("Exiting Calculator. Goodbye!")
            break

if __name__ == "__main__":
    calculator()


# Password Generator
import random
import string

def generate_password(length):
    """Generates a random password of the given length."""
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

if __name__ == "__main__":
    print("Welcome to the Password Generator!")
    while True:  # Loop to keep generating passwords if the user wants
        try:
            length = int(input("Enter the password length: "))
            if length > 0:
                password = generate_password(length)
                print(f"Generated Password: {password}")
            else:
                print("Length must be greater than 0!")
        except ValueError:
            print("Invalid input! Please enter a valid number.")

        # Ask if the user wants to generate another password
        again = input("Do you want to generate another password? (yes/no): ").lower()
        if again != "yes":
            print("Thank you for using the Password Generator! Goodbye.")
            break



# Rock-Paper-Secissors Game
import random

def play_game():
    options = ["rock", "paper", "scissors"]
    user_score = 0
    computer_score = 0

    print("Welcome to Rock-Paper-Scissors!")
    while True:
        print("\nChoose: rock, paper, or scissors")
        user_choice = input("Your choice: ").lower()
        if user_choice not in options:
            print("Invalid choice! Please try again.")
            continue

        computer_choice = random.choice(options)
        print(f"Computer's choice: {computer_choice}")

        # Determine the winner
        if user_choice == computer_choice:
            print("It's a tie!")
        elif (user_choice == "rock" and computer_choice == "scissors") or \
             (user_choice == "paper" and computer_choice == "rock") or \
             (user_choice == "scissors" and computer_choice == "paper"):
            print("You win this round!")
            user_score += 1
        else:
            print("Computer wins this round!")
            computer_score += 1

        print(f"Score: You {user_score} - {computer_score} Computer")

        # Ask if user wants to play again
        play_again = input("Do you want to play again? (yes/no): ").lower()
        if play_again != "yes":
            print("Thanks for playing Rock-Paper-Scissors!")
            break

if __name__ == "__main__":
    play_game()


# contacts book

contacts = []
def add_contact(name, phone, email, address):
    contact = {
        "name": name,
        "phone": phone,
        "email": email,
        "address": address
    }
    contacts.append(contact)
    print("Contact added successfully!")

def view_contacts():
    if not contacts:
        print("Your contact book is empty!")
    else:
        print("\nContact List:")
        for idx, contact in enumerate(contacts):
            print(f"{idx + 1}. Name: {contact['name']}, Phone: {contact['phone']}")
def search_contact(query):
    results = [contact for contact in contacts if query.lower() in contact['name'].lower() or query in contact['phone']]
    if results:
        print("\nSearch Results:")
        for contact in results:
            print(f"Name: {contact['name']}, Phone: {contact['phone']}, Email: {contact['email']}, Address: {contact['address']}")
    else:
        print("No matching contact found!")
def update_contact(index, name, phone, email, address):
    if 0 <= index < len(contacts):
        contacts[index] = {"name": name, "phone": phone, "email": email, "address": address}
        print("Contact updated successfully!")
    else:
        print("Invalid contact number!")
def delete_contact(index):
    if 0 <= index < len(contacts):
        removed_contact = contacts.pop(index)
        print(f"Deleted contact: {removed_contact['name']}")
    else:
        print("Invalid contact number!")
if __name__ == "__main__":
    print("Welcome to the Contact Book App!")
    while True:
        print("\n1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        try:
            choice = int(input("Choose an option (1-6): "))
            if choice == 1:
                name = input("Enter name: ")
                phone = input("Enter phone: ")
                email = input("Enter email: ")
                address = input("Enter address: ")
                add_contact(name, phone, email, address)
            elif choice == 2:
                view_contacts()
            elif choice == 3:
                query = input("Enter name or phone to search: ")
                search_contact(query)
            elif choice == 4:
                view_contacts()
                idx = int(input("Enter contact number to update: ")) - 1
                name = input("Enter new name: ")
                phone = input("Enter new phone: ")
                email = input("Enter new email: ")
                address = input("Enter new address: ")
                update_contact(idx, name, phone, email, address)
            elif choice == 5:
                view_contacts()
                idx = int(input("Enter contact number to delete: ")) - 1
                delete_contact(idx)
            elif choice == 6:
                print("Exiting Contact Book. Goodbye!")
                break
            else:
                print("Invalid choice! Please try again.")
        except ValueError:
            print("Invalid input! Please enter a number.")
