# dnd-character-gen
Randomized answers for DnD character race, class, and background categories, as well as generate the power stats of the character sheet.
import tkinter as tk
import random

# List of D&D character classes
character_classes = [
    "Barbarian", "Bard", "Cleric", "Druid", "Fighter",
    "Monk", "Paladin", "Ranger", "Rogue", "Sorcerer",
    "Warlock", "Wizard"
]

# List of D&D character races
character_races = [
    "Human", "Elf", "Dwarf", "Halfling", "Dragonborn",
    "Gnome", "Half-Elf", "Half-Orc", "Tiefling", "Aasimar"
]

# List of D&D character backgrounds
character_backgrounds = [
    "Acolyte", "Charlatan", "Criminal", "Entertainer",
    "Folk Hero", "Guild Artisan", "Hermit", "Noble",
    "Outlander", "Sage", "Sailor", "Soldier", "Urchin"
]

# Store results
results = []

# Function to generate a random class
def generate_class():
    random_class = random.choice(character_classes)
    results.append(f"Your character class is: {random_class}")
    update_results()

# Function to generate a random race
def generate_race():
    random_race = random.choice(character_races)
    results.append(f"Your character race is: {random_race}")
    update_results()

# Function to generate a random background
def generate_background():
    random_background = random.choice(character_backgrounds)
    results.append(f"Your character background is: {random_background}")
    update_results()

# Function to generate random ability scores
def generate_stats():
    stats = {
        "Strength": random.randint(1, 20),
        "Dexterity": random.randint(1, 20),
        "Constitution": random.randint(1, 20),
        "Intelligence": random.randint(1, 20),
        "Wisdom": random.randint(1, 20),
        "Charisma": random.randint(1, 20),
    }
    stats_str = "\n".join([f"{key}: {value}" for key, value in stats.items()])
    results.append(f"Your character stats are:\n{stats_str}")
    update_results()

# Function to update the results display
def update_results():
    result_label.config(text="\n".join(results))

# Function to reset results
def reset_results():
    results.clear()
    result_label.config(text="")

# Create the main application window
root = tk.Tk()
root.title("Random D&D Character Generator")

# Create a button that generates a class
generate_class_button = tk.Button(root, text="Generate Class", command=generate_class)
generate_class_button.pack(pady=10)

# Create a button that generates a race
generate_race_button = tk.Button(root, text="Generate Race", command=generate_race)
generate_race_button.pack(pady=10)

# Create a button that generates a background
generate_background_button = tk.Button(root, text="Generate Background", command=generate_background)
generate_background_button.pack(pady=10)

# Create a button that generates stats
generate_stats_button = tk.Button(root, text="Generate Character Stats", command=generate_stats)
generate_stats_button.pack(pady=10)

# Create a reset button
reset_button = tk.Button(root, text="Generate a New Character", command=reset_results)
reset_button.pack(pady=10)

# Label to display the result
result_label = tk.Label(root, text="", font=("Helvetica", 16))
result_label.pack(pady=20)

# Run the application
root.mainloop()
