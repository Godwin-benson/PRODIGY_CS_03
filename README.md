import re

def check_password_strength(password):
    # Criteria for a strong password
    min_length = 12  # Set minimum password length to 12 characters
    uppercase = r'[A-Z]'
    lowercase = r'[a-z]'
    digits = r'[0-9]'
    special_characters = r'[\W_]'  # Non-alphanumeric characters, including special chars

    # Initialize feedback list
    feedback = []

    # Check password length
    if len(password) < min_length:
        feedback.append(f"Password must be at least {min_length} characters long.")
    else:
        feedback.append("Password length is sufficient.")

    # Check for at least one uppercase letter
    if not re.search(uppercase, password):
        feedback.append("Password must contain at least one uppercase letter.")
    else:
        feedback.append("Password contains at least one uppercase letter.")

    # Check for at least one lowercase letter
    if not re.search(lowercase, password):
        feedback.append("Password must contain at least one lowercase letter.")
    else:
        feedback.append("Password contains at least one lowercase letter.")

    # Check for at least one digit
    if not re.search(digits, password):
        feedback.append("Password must contain at least one digit.")
    else:
        feedback.append("Password contains at least one digit.")

    # Check for at least one special character
    if not re.search(special_characters, password):
        feedback.append("Password must contain at least one special character (e.g., !, @, #, $, etc.).")
    else:
        feedback.append("Password contains at least one special character.")

    # Provide overall strength rating
    if len(feedback) == 5:
        strength = "Strong password!"
    else:
        strength = "Weak password."

    return feedback, strength


# Sample usage
password = input("Enter your password to check its strength: ")
feedback, strength = check_password_strength(password)

# Print feedback and strength
print("\nPassword Strength Check:")
for line in feedback:
    print(line)
print("\nOverall Strength:", strength)
