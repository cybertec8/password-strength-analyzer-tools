# task 2 password-strength-analyzer-tools
A strong password, with a combination of upper and lowercase letters, numbers, and special characters, is much harder for attackers to guess compared to simple passwords like "password123." These tools help you create passwords that are difficult to crack.

import re

def password_strength(password):
    # Criteria
    length_criteria = len(password) >= 8
    lower_case = re.search(r'[a-z]', password)
    upper_case = re.search(r'[A-Z]', password)
    digits = re.search(r'[0-9]', password)
    special_characters = re.search(r'[@#$%^&+=!]', password)

    # Evaluation
    if len(password) == 0:
        return "Password cannot be empty"
    
    if not length_criteria:
        return "Password should be at least 8 characters long"
    
    score = 0

    # Length
    if len(password) >= 12:
        score += 1

    # Lowercase letter
    if lower_case:
        score += 1

    # Uppercase letter
    if upper_case:
        score += 1

    # Digit
    if digits:
        score += 1

    # Special character
    if special_characters:
        score += 1

    # Scoring logic
    if score == 5:
        return "Password is Very Strong"
    elif score == 4:
        return "Password is Strong"
    elif score == 3:
        return "Password is Medium"
    elif score == 2:
        return "Password is Weak"
    else:
        return "Password is Very Weak"

# Test the function
password = input("Enter a password to analyze: ")
print(password_strength(password))
