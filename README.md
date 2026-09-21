def add(a, b):
    return a + b


def subtract(a, b):
    return a - b


def multiply(a, b):
    return a * b


def divide(a, b):
    if b == 0:
        return "Error: Division by zero is not allowed"
    return a / b


def modulus(a, b):
    if b == 0:
        return "Error: Modulus by zero is not allowed"
    return a % b


def get_number(prompt):
    """Keep asking until the user enters a valid number."""
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a number.")


def main():
    operations = {
        "1": ("Addition", "+", add),
        "2": ("Subtraction", "-", subtract),
        "3": ("Multiplication", "*", multiply),
        "4": ("Division", "/", divide),
        "5": ("Modulus", "%", modulus),
    }

    print("=== Simple Calculator ===")
    while True:
        print("\n1. Addition (+)")
        print("2. Subtraction (-)")
        print("3. Multiplication (*)")
        print("4. Division (/)")
        print("5. Modulus (%)")
        print("0. Exit")

        choice = input("Choose an operation: ").strip()

        if choice == "0":
            print("Goodbye!")
            break
        if choice not in operations:
            print("Invalid choice. Please select 0-5.")
            continue

        a = get_number("Enter first number: ")
        b = get_number("Enter second number: ")

        name, symbol, func = operations[choice]
        result = func(a, b)

        if isinstance(result, str):
            print(f"\n{name}: {result}")
        else:
            print(f"\n{name}: {a:g} {symbol} {b:g} = {result:g}")


if __name__ == "__main__":
    main()
