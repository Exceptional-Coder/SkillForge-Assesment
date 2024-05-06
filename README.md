def decrypt_caesar(ciphertext, shift):
    decrypted_text = ""
    for char in ciphertext:
        if char.isalpha():
            # Determine if the character is uppercase or lowercase
            if char.isupper():
                decrypted_char = chr((ord(char) - ord('A') - shift) % 26 + ord('A'))
            else:
                decrypted_char = chr((ord(char) - ord('a') - shift) % 26 + ord('a'))
            decrypted_text += decrypted_char
        else:
            # Non-alphabetic characters remain unchanged
            decrypted_text += char
    return decrypted_text

# Function to crack the Caesar cipher using the clue provided
def crack_caesar(ciphertext, clue):
    # Convert the clue to lowercase for case insensitivity
    clue = clue.lower()
    # Search for a number indicating the Caesar shift
    shift = None
    for word in clue.split():
        if word.isdigit():
            shift = int(word)
            break
    if shift is None:
        return "Could not determine Caesar shift from the clue."
    # Decrypt the ciphertext using the determined shift
    decrypted_text = decrypt_caesar(ciphertext, shift)
    return decrypted_text

# Provided ciphertext and clue
ciphertext = "vhixoieemksktorywzvhxzijqni"
clue = "Caesar is everything. But he took it to the next level."

# Decrypt the ciphertext using the provided clue
plaintext = crack_caesar(ciphertext, clue)
print("Decrypted text:", plaintext)

