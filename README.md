# leadzen.ai-assignment-3
class Expense:
    def __init__(self, amount, category, date):
        self.amount = amount
        self.category = category
        self.date = date

class ExpenseTracker:
    def __init__(self):
        self.expenses = []

    def add_expense(self, amount, category, date):
        expense = Expense(amount, category, date)
        self.expenses.append(expense)

    def view_expenses(self):
        if not self.expenses:
            print("No expenses recorded yet.")
            return
        for expense in self.expenses:
            print(f"Date: {expense.date}, Amount: {expense.amount}, Category: {expense.category}")

    def view_spending_patterns(self):
        categories = {}
        for expense in self.expenses:
            if expense.category in categories:
                categories[expense.category] += expense.amount
            else:
                categories[expense.category] = expense.amount
        print("Spending Patterns:")
        for category, total_amount in categories.items():
            print(f"{category}: {total_amount}")

def main():
    tracker = ExpenseTracker()
    while True:
        print("\nExpense Tracking System")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. View Spending Patterns")
        print("4. Exit")
        choice = input("Enter your choice: ")

        if choice == '1':
            amount = float(input("Enter the amount: "))
            category = input("Enter the category: ")
            date = input("Enter the date (YYYY-MM-DD): ")
            tracker.add_expense(amount, category, date)
            print("Expense added successfully!")
        elif choice == '2':
            tracker.view_expenses()
        elif choice == '3':
            tracker.view_spending_patterns()
        elif choice == '4':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please enter a valid option.")

if __name__ == "__main__":
    main()
