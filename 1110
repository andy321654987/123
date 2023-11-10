import random
import xml.etree.ElementTree as ET

def load_settings():
    try:
        tree = ET.parse('setting.xml')
        root = tree.getroot()
        x1 = int(root.find('x1').text)
        x2 = int(root.find('x2').text)
        n = int(root.find('n').text)
        return x1, x2, n
    except Exception as e:
        print(f"Error loading settings: {e}")
        return None

def save_settings(x1, x2, n):
    root = ET.Element("settings")
    ET.SubElement(root, "x1").text = str(x1)
    ET.SubElement(root, "x2").text = str(x2)
    ET.SubElement(root, "n").text = str(n)
    tree = ET.ElementTree(root)
    tree.write('setting.xml')

def play_game():
    x1, x2, n = load_settings()

    if x1 is None:
        return

    target_number = random.randint(x1, x2)
    attempts = 0

    while attempts < n:
        guess = int(input(f"Guess the number between {x1} and {x2}: "))
        attempts += 1

        if guess == target_number:
            print(f"Congratulations! You guessed the correct number {target_number} in {attempts} attempts.")
            break
        elif guess < target_number:
            print("Too low. Try again.")
        else:
            print("Too high. Try again.")

    if attempts == n:
        print(f"Sorry, you've reached the maximum number of attempts. The correct number was {target_number}.")

if __name__ == "__main__":
    play_game()
