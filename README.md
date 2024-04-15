import random
import string

def generate_password(length):
    """Generate a random password with the specified length."""
    # Define characters to use in the password
    characters = string.ascii_letters + string.digits + string.punctuation

    # Generate the password
    password = ''.join(random.choice(characters) for _ in range(length))

    return password

def main():
    print("Welcome to the Python Password Generator!")
    while True:
        try:
            num_passwords = int(input("How many passwords do you want to generate? "))
            if num_passwords <= 0:
                print("Please enter a number greater than zero.")
                continue
            print(f"Generating {num_passwords} passwords")
            passwords = []
            for i in range(num_passwords):
                while True:
                    try:
                        length = int(input(f"Enter the length of Password ( minimum length of the password 3 )#{i + 1}: "))
                        if length < 3:
                            print("Minimum length of password should be 3.")
                        else:
                            passwords.append(generate_password(length))
                            break
                    except ValueError:
                        print("Invalid input. Please enter a valid integer.")
            print("\nGenerated Passwords:")
            for i, password in enumerate(passwords, 1):
                print(f"Password {i}: {password}")
            break
        except ValueError:
            print("Invalid input. Please enter a valid integer for the number of passwords.")

if __name__ == "__main__":
    main()
