import os
import random
import string

generated_codes = set()

ascii_art = """
\033[93m
 ____       _                   ____          _           
|  _ \ ___ | |__  _   ___  __  / ___|___   __| | ___  ___ 
| |_) / _ \| '_ \| | | \ \/ / | |   / _ \ / _` |/ _ \/ __|
|  _ < (_) | |_) | |_| |>  <  | |__| (_) | (_| |  __/\__ \\
|_| \_\___/|_.__/ \__,_/_/\_\  \____\___/ \__,_|\___||___/
===========================================================                                                           
\033[0m
"""

def generate_gift_card_code():
    code = '-'.join(''.join(random.choices(string.ascii_uppercase + string.digits, k=4)) for _ in range(3))
    while code in generated_codes:
        code = '-'.join(''.join(random.choices(string.ascii_uppercase + string.digits, k=4)) for _ in range(3))
    generated_codes.add(code)
    return code

def print_valid_code(code):
    if random.random() < 0.80:
        code_hidden = code[:-2] + '**'
        print(f"\033[91m[-] INVALID | {code_hidden}\033[0m")
    else:
        code_hidden = code[:-2] + '**'
        print(f"\033[92m[+] VALID | {code_hidden}\033[0m")

def main():
    os.system('cls' if os.name == 'nt' else 'clear')
    print(ascii_art)
    num_cards = int(input("How Many Robux Codes?: "))
        
    for _ in range(num_cards):
        code = generate_gift_card_code()
        print_valid_code(code)

    message = "(Valid Codes Been Put In Valid-Codes.txt & Invalid Codes Been Added To Invalid-Codes.txt)"
    print("\033[91m\033[93m\033[92m\033[96m\033[94m\033[95m" + message + "\033[0m")
    print("-" * len(message))

if __name__ == "__main__":
    main()
