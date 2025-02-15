category."""
        summary = {}
        for expense in self.expenses:
            category = expense["category"]
            summary[category] = summary.get(category, 0) + expense["amount"]
        
        print("\nCategory-wise Expenses:")
        for category, total in summary.items():
            print(f"{category}: ${total:.2f}")
    
    def monthly_summary(self):
        """Show total expenses per month."""
        monthly = {}
        for expense in self.expenses:
            month = expense["date"][:7]  # YYYY-MM format
            monthly[month] = monthly.get(month, 0) + expense["amount"]
        
        print("\nMonthly Expenses:")
        for month, total in monthly.items():
            print(f"{month}: ${total:.2f}")

if __name__ == "__main__":
    tracker = ExpenseTracker()
    while True:
        print("\nExpense Tracker")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. View Category-wise Summary")
        print("4. View Monthly Summary")
        print("5. Exit")
        choice = input("Choose an option: ")
        
        if choice == '1':
            amount = input("Enter amount: ")
            category = input("Enter category: ")
            description = input("Enter description: ")
            tracker.add_expense(amount, category, description)
        elif choice == '2':
            tracker.view_expenses()
        elif choice == '3':
            tracker.category_summary()
        elif choice == '4':
            tracker.monthly_summary()
        elif choice == '5':
            print("Exiting Expense Tracker. Goodbye!")
            break
        else:
            print("Invalid option. Please try again.")
