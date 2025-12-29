import os

FILE_NAME = "library.txt"

def add_book():
    book_id = input("Enter Book ID: ")
    title = input("Enter Book Title: ")
    author = input("Enter Author Name: ")

    with open(FILE_NAME, "a") as file:
        file.write(f"{book_id},{title},{author},Available\n")

    print("Book added successfully!")

def view_books():
    if not os.path.exists(FILE_NAME):
        print("No books available.")
        return

    with open(FILE_NAME, "r") as file:
        print("\nBook ID | Title | Author | Status")
        print("-" * 40)
        for line in file:
            book_id, title, author, status = line.strip().split(",")
            print(f"{book_id} | {title} | {author} | {status}")

def search_book():
    keyword = input("Enter title or author to search: ").lower()

    found = False
    with open(FILE_NAME, "r") as file:
        for line in file:
            if keyword in line.lower():
                print(line.strip())
                found = True

    if not found:
        print("Book not found.")

def issue_book():
    book_id = input("Enter Book ID to issue: ")
    updated_lines = []

    with open(FILE_NAME, "r") as file:
        for line in file:
            data = line.strip().split(",")
            if data[0] == book_id and data[3] == "Available":
                data[3] = "Issued"
                print("Book issued successfully!")
            updated_lines.append(",".join(data) + "\n")

    with open(FILE_NAME, "w") as file:
        file.writelines(updated_lines)

def return_book():
    book_id = input("Enter Book ID to return: ")
    updated_lines = []

    with open(FILE_NAME, "r") as file:
        for line in file:
            data = line.strip().split(",")
            if data[0] == book_id and data[3] == "Issued":
                data[3] = "Available"
                print("Book returned successfully!")
            updated_lines.append(",".join(data) + "\n")

    with open(FILE_NAME, "w") as file:
        file.writelines(updated_lines)

def main():
    while True:
        print("\n--- Library Management System ---")
        print("1. Add Book")
        print("2. View Books")
        print("3. Search Book")
        print("4. Issue Book")
        print("5. Return Book")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            add_book()
        elif choice == "2":
            view_books()
        elif choice == "3":
            search_book()
        elif choice == "4":
            issue_book()
        elif choice == "5":
            return_book()
        elif choice == "6":
            print("Exiting system. Goodbye!")
            break
        else:
            print("Invalid choice. Try again.")

main()
