import time

def introduction():
    print("Welcome to 'Quest for the Enchanted Realm'!")
    print("You stand at the edge of the village, ready to begin your quest.")
    print("The forest looms before you, its ancient trees whispering tales of the enchanted realm.")

def make_choice():
    print("\nWhat path will you choose?")
    print("1. Take the left path.")
    print("2. Take the right path.")

    choice = input("Enter your choice (1 or 2): ")
    return choice

def left_path():
    print("\nYou chose the left path. The trail winds deeper into the heart of the forest.")
    time.sleep(2)
    print("Suddenly, you encounter a mystical creature with shimmering scales and a wise expression.")
    time.sleep(2)
    print("The creature offers you guidance and a magical amulet that glows with a soft light.")

def right_path():
    print("\nYou chose the right path. The path is overgrown with thick vegetation, and the air is filled with mysterious whispers.")
    time.sleep(2)
    print("You stumble upon an ancient shrine with a riddle written on it. Solve the riddle to proceed.")

    # You can add more gameplay elements, such as a riddle-solving function here.

if __name__ == "__main__":
    introduction()

    while True:
        choice = make_choice()

        if choice == '1':
            left_path()
            break
        elif choice == '2':
            right_path()
            break
        else:
            print("Invalid choice. Please enter 1 or 2.")
import time
import random

def introduction():
    print("Welcome to 'Quest for the Enchanted Realm'!")
    print("You stand at the edge of the village, ready to begin your quest.")
    print("The forest looms before you, its ancient trees whispering tales of the enchanted realm.")

def make_choice():
    print("\nWhat path will you choose?")
    print("1. Take the left path.")
    print("2. Take the right path.")
    print("3. Venture into the mysterious caves.")

    choice = input("Enter your choice (1, 2, or 3): ")
    return choice

def left_path():
    print("\nYou chose the left path. The trail winds deeper into the heart of the forest.")
    time.sleep(2)
    print("Suddenly, you encounter a mystical creature with shimmering scales and a wise expression.")
    time.sleep(2)
    print("The creature offers you guidance and a magical amulet that glows with a soft light.")
    time.sleep(2)
    print("You continue on your journey with the creature's blessing.")

def right_path():
    print("\nYou chose the right path. The path is overgrown with thick vegetation, and the air is filled with mysterious whispers.")
    time.sleep(2)
    print("You stumble upon an ancient shrine with a riddle written on it. Solve the riddle to proceed.")
    
    # You can add a riddle-solving function here for more interactivity.

def mysterious_caves():
    print("\nYou decide to explore the mysterious caves near the village.")
    time.sleep(2)
    print("As you delve deeper, you encounter a group of friendly dwarves.")
    time.sleep(2)
    print("They invite you to join them in a game of riddles. Win, and they'll share the secrets of the enchanted realm.")

    # You can add a riddle-solving game with the dwarves here.

def main():
    introduction()

    while True:
        choice = make_choice()

        if choice == '1':
            left_path()
            break
        elif choice == '2':
            right_path()
            break
        elif choice == '3':
            mysterious_caves()
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()
import random
import time

class Player:
    def __init__(self, name, health, attack, defense):
        self.name = name
        self.health = health
        self.attack = attack
        self.defense = defense

class Enemy:
    def __init__(self, name, health, attack, defense):
        self.name = name
        self.health = health
        self.attack = attack
        self.defense = defense

def create_character():
    print("Welcome to the RPG Adventure!")
    name = input("Enter your character's name: ")
    return Player(name, health=100, attack=10, defense=5)

def create_enemy():
    enemy_names = ["Goblin", "Skeleton", "Orc"]
    enemy_name = random.choice(enemy_names)
    return Enemy(enemy_name, health=random.randint(20, 50), attack=random.randint(5, 15), defense=random.randint(1, 5))

def explore(player):
    print(f"{player.name}, you embark on a journey to explore the unknown...")
    time.sleep(2)
    
    enemy = create_enemy()
    print(f"Uh-oh! You encounter a {enemy.name}!")

    while player.health > 0 and enemy.health > 0:
        print("\n--- Battle Menu ---")
        print("1. Attack")
        print("2. Defend")
        print("3. Run away")

        choice = input("Enter your choice (1, 2, or 3): ")

        if choice == '1':
            player_attack = player.attack + random.randint(-2, 2)
            enemy_defense = enemy.defense + random.randint(-1, 1)
            damage = max(0, player_attack - enemy_defense)
            enemy.health -= damage
            print(f"You attack the {enemy.name} and deal {damage} damage!")
        elif choice == '2':
            player_defense = player.defense + random.randint(-1, 1)
            print(f"You defend, increasing your defense for the next turn.")
        elif choice == '3':
            print("You attempt to run away.")
            if random.random() < 0.7:
                print("You successfully escape!")
                return
            else:
                print("Escape failed! The enemy attacks you.")

        if enemy.health > 0:
            enemy_attack = enemy.attack + random.randint(-2, 2)
            player_defense = player.defense + random.randint(-1, 1)
            damage = max(0, enemy_attack - player_defense)
            player.health -= damage
            print(f"The {enemy.name} attacks you and deals {damage} damage!")

        print(f"\n{player.name}'s Health: {player.health} | {enemy.name}'s Health: {enemy.health}")

    if player.health <= 0:
        print("Game Over! You were defeated.")
    else:
        print(f"You defeated the {enemy.name} and gained experience points!")

def main():
    player = create_character()
    explore(player)

if __name__ == "__main__":
    main()import random
import time

class Player:
    def __init__(self, name, level, experience, health, attack, defense, inventory):
        self.name = name
        self.level = level
        self.experience = experience
        self.health = health
        self.attack = attack
        self.defense = defense
        self.inventory = inventory

    def display_stats(self):
        print(f"\n--- {self.name}'s Stats ---")
        print(f"Level: {self.level}")
        print(f"Experience: {self.experience}")
        print(f"Health: {self.health}")
        print(f"Attack: {self.attack}")
        print(f"Defense: {self.defense}")
        print(f"Inventory: {', '.join(self.inventory)}")

class Enemy:
    def __init__(self, name, health, attack, defense, experience_reward, loot):
        self.name = name
        self.health = health
        self.attack = attack
        self.defense = defense
        self.experience_reward = experience_reward
        self.loot = loot

def create_character():
    print("Welcome to the RPG Adventure!")
    name = input("Enter your character's name: ")
    return Player(name, level=1, experience=0, health=100, attack=10, defense=5, inventory=[])

def create_enemy():
    enemy_data = {
        "Goblin": {"health": 30, "attack": 8, "defense": 3, "experience_reward": 20, "loot": ["Health Potion", "Dagger"]},
        "Skeleton": {"health": 40, "attack": 10, "defense": 5, "experience_reward": 30, "loot": ["Mana Potion", "Short Sword"]},
        "Orc": {"health": 50, "attack": 12, "defense": 7, "experience_reward": 40, "loot": ["Strength Elixir", "Battle Axe"]}
    }

    enemy_name = random.choice(list(enemy_data.keys()))
    enemy_stats = enemy_data[enemy_name]
    return Enemy(enemy_name, **enemy_stats)

def explore(player):
    print(f"{player.name}, you embark on a journey to explore the unknown...")

    while player.health > 0:
        enemy = create_enemy()
        print(f"\nUh-oh! You encounter a {enemy.name}!")
        
        while player.health > 0 and enemy.health > 0:
            print("\n--- Battle Menu ---")
            print("1. Attack")
            print("2. Defend")
            print("3. Run away")

            choice = input("Enter your choice (1, 2, or 3): ")

            if choice == '1':
                player_attack = player.attack + random.randint(-2, 2)
                enemy_defense = enemy.defense + random.randint(-1, 1)
                damage = max(0, player_attack - enemy_defense)
                enemy.health -= damage
                print(f"You attack the {enemy.name} and deal {damage} damage!")
            elif choice == '2':
                player_defense = player.defense + random.randint(-1, 1)
                print(f"You defend, increasing your defense for the next turn.")
            elif choice == '3':
                print("You attempt to run away.")
                if random.random() < 0.7:
                    print("You successfully escape!")
                    break
                else:
                    print("Escape failed! The enemy attacks you.")

            if enemy.health > 0:
                enemy_attack = enemy.attack + random.randint(-2, 2)
                player_defense = player.defense + random.randint(-1, 1)
                damage = max(0, enemy_attack - player_defense)
                player.health -= damage
                print(f"The {enemy.name} attacks you and deals {damage} damage!")

            print(f"\n{player.name}'s Health: {player.health} | {enemy.name}'s Health: {enemy.health}")

        if player.health > 0:
            player.experience += enemy.experience_reward
            player.inventory.extend(enemy.loot)
            player.display_stats()

            print(f"You defeated the {enemy.name} and gained {enemy.experience_reward} experience points!")
            print(f"You looted: {', '.join(enemy.loot)}")

            level_up(player)
            
            print("\nDo you want to continue exploring?")
            explore_choice = input("Enter 'yes' or 'no': ")
            if explore_choice.lower() != 'yes':
                print("Thanks for playing!")
                break

        else:
            print("Game Over! You were defeated.")
            break

def level_up(player):
    if player.experience >= player.level * 50:
        player.level += 1
        player.health += 20
        player.attack += 5
        player.defense += 2
        print(f"\nCongratulations! You leveled up to Level {player.level}!")
        player.display_stats()

def main():
    player = create_character()
    explore(player)

if __name__ == "__main__":
    main()import random
import time

class Player:
    def __init__(self, name, level, experience, health, max_health, attack, defense, gold, inventory):
        self.name = name
        self.level = level
        self.experience = experience
        self.health = health
        self.max_health = max_health
        self.attack = attack
        self.defense = defense
        self.gold = gold
        self.inventory = inventory

    def display_stats(self):
        print(f"\n--- {self.name}'s Stats ---")
        print(f"Level: {self.level}")
        print(f"Experience: {self.experience}")
        print(f"Health: {self.health}/{self.max_health}")
        print(f"Attack: {self.attack}")
        print(f"Defense: {self.defense}")
        print(f"Gold: {self.gold}")
        print(f"Inventory: {', '.join(self.inventory)}")

    def heal(self, amount):
        self.health = min(self.max_health, self.health + amount)

class Enemy:
    def __init__(self, name, health, max_health, attack, defense, experience_reward, gold_reward, loot):
        self.name = name
        self.health = health
        self.max_health = max_health
        self.attack = attack
        self.defense = defense
        self.experience_reward = experience_reward
        self.gold_reward = gold_reward
        self.loot = loot

def create_character():
    print("Welcome to the RPG Adventure!")
    name = input("Enter your character's name: ")
    return Player(name, level=1, experience=0, health=100, max_health=100, attack=10, defense=5, gold=50, inventory=[])

def create_enemy():
    enemy_data = {
        "Goblin": {"health": 30, "max_health": 30, "attack": 8, "defense": 3, "experience_reward": 20, "gold_reward": 10, "loot": ["Health Potion", "Dagger"]},
        "Skeleton": {"health": 40, "max_health": 40, "attack": 10, "defense": 5, "experience_reward": 30, "gold_reward": 15, "loot": ["Mana Potion", "Short Sword"]},
        "Orc": {"health": 50, "max_health": 50, "attack": 12, "defense": 7, "experience_reward": 40, "gold_reward": 20, "loot": ["Strength Elixir", "Battle Axe"]}
    }

    enemy_name = random.choice(list(enemy_data.keys()))
    enemy_stats = enemy_data[enemy_name]
    return Enemy(enemy_name, **enemy_stats)

def explore(player):
    print(f"{player.name}, you embark on a journey to explore the unknown...")

    while player.health > 0:
        enemy = create_enemy()
        print(f"\nUh-oh! You encounter a {enemy.name}!")
        
        while player.health > 0 and enemy.health > 0:
            print("\n--- Battle Menu ---")
            print("1. Attack")
            print("2. Defend")
            print("3. Use Item")
            print("4. Run away")

            choice = input("Enter your choice (1, 2, 3, or 4): ")

            if choice == '1':
                player_attack = player.attack + random.randint(-2, 2)
                enemy_defense = enemy.defense + random.randint(-1, 1)
                damage = max(0, player_attack - enemy_defense)
                enemy.health = max(0, enemy.health - damage)
                print(f"You attack the {enemy.name} and deal {damage} damage!")
            elif choice == '2':
                player_defense = player.defense + random.randint(-1, 1)
                print(f"You defend, increasing your defense for the next turn.")
            elif choice == '3':
                use_item(player)
            elif choice == '4':
                print("You attempt to run away.")
                if random.random() < 0.7:
                    print("You successfully escape!")
                    break
                else:
                    print("Escape failed! The enemy attacks you.")

            if enemy.health > 0:
                enemy_attack = enemy.attack + random.randint(-2, 2)
                player_defense = player.defense + random.randint(-1, 1)
                damage = max(0, enemy_attack - player_defense)
                player.health = max(0, player.health - damage)
                print(f"The {enemy.name} attacks you and deals {damage} damage!")

            print(f"\n{player.name}'s Health: {player.health}/{player.max_health} | {enemy.name}'s Health: {enemy.health}/{enemy.max_health}")

        if player.health > 0:
            player.experience += enemy.experience_reward
            player.gold += enemy.gold_reward
            player.inventory.extend(enemy.loot)
            player.display_stats()

            print(f"You defeated the {enemy.name} and gained {enemy.experience_reward} experience points!")
            print(f"You looted: {', '.join(enemy.loot)}")
            print(f"You earned {enemy.gold_reward} gold.")

            level_up(player)
            shop_menu(player)

            print("\nDo you want to continue exploring?")
            explore_choice = input("Enter 'yes' or 'no': ")
            if explore_choice.lower() != 'yes':
                print("Thanks for playing!")
                break

        else:
            print("Game Over! You were defeated.")
            break

def use_item(player):
    if not player.inventory:
        print("Your inventory is empty.")
        return

    print("\n--- Inventory ---")
    for i, item in enumerate(player.inventory, 1):
        print(f"{i}. {item}")

    choice = input("Enter the number of the item to use (or enter '0' to go back): ")

    if choice.isdigit():
        choice = int(choice)
        if 0 < choice <= len(player.inventory):
            item_used = player.inventory.pop(choice - 1)
            if "Health Potion" in item_used:
                heal_amount = random.randint(10, 20)
                player.heal(heal_amount)
                print(f"You used a Health Potion and healed for {heal_amount} health.")
            elif "Mana Potion" in item_used:
                # You can add more effects for different items
                print("You used a Mana Potion.")
            else:
                print("You used the item.")
            player.display_stats()

def level_up(player):
    while player.experience >= player.level * 50:
        player.level += 1
        player.max_health += 20
        player.health = player.max_health
        player.attack += 5
        player.defense += 2
        print(f"\nCongratulations! You leveled up to Level {player.level}!")
        player.display_stats()

def shop_menu(player):
    print("\n--- Shop ---")
    print("1. Heal (Cost: 10 gold)")
    print("2. Buy Potion (Cost: 5 gold)")
    print("3. Leave the shop")

    choice = input("Enter your choice (1, 2, or 3): ")

    if choice == '1':
        if player.gold >= 10:
            player.gold -= 10
            player.heal(30)
            print("You paid 10 gold to heal.")
        else:
            print("You don't have enough gold to heal.")
    elif choice == '2':
        if player.gold >= 5:
            player.gold -= 5
            player.inventory.append("Health Potion")
            print("You bought a Health Potion for 5 gold.")
        else:
            print("You don't have enough gold to buy a Health Potion.")
    elif choice == '3':
        print("You leave the shop.")

def main():
    player = create_character()
    explore(player)

if __name__ == "__main__":
    main()
import random
import time

class Player:
    def __init__(self, name, level, experience, health, max_health, attack, defense, gold, inventory, player_class):
        self.name = name
        self.level = level
        self.experience = experience
        self.health = health
        self.max_health = max_health
        self.attack = attack
        self.defense = defense
        self.gold = gold
        self.inventory = inventory
        self.player_class = player_class

    def display_stats(self):
        print(f"\n--- {self.name}'s Stats ---")
        print(f"Class: {self.player_class}")
        print(f"Level: {self.level}")
        print(f"Experience: {self.experience}")
        print(f"Health: {self.health}/{self.max_health}")
        print(f"Attack: {self.attack}")
        print(f"Defense: {self.defense}")
        print(f"Gold: {self.gold}")
        print(f"Inventory: {', '.join(self.inventory)}")

    def heal(self, amount):
        self.health = min(self.max_health, self.health + amount)

class Enemy:
    def __init__(self, name, health, max_health, attack, defense, experience_reward, gold_reward, loot):
        self.name = name
        self.health = health
        self.max_health = max_health
        self.attack = attack
        self.defense = defense
        self.experience_reward = experience_reward
        self.gold_reward = gold_reward
        self.loot = loot

class Quest:
    def __init__(self, name, description, reward_experience, reward_gold):
        self.name = name
        self.description = description
        self.reward_experience = reward_experience
        self.reward_gold = reward_gold

def create_character():
    print("Welcome to the RPG Adventure!")
    name = input("Enter your character's name: ")

    print("\nChoose your class:")
    print("1. Warrior")
    print("2. Mage")
    print("3. Rogue")
    class_choice = input("Enter the number of your class choice (1, 2, or 3): ")

    if class_choice == '1':
        player_class = "Warrior"
        player = Player(name, level=1, experience=0, health=100, max_health=100, attack=15, defense=8, gold=50, inventory=[], player_class=player_class)
    elif class_choice == '2':
        player_class = "Mage"
        player = Player(name, level=1, experience=0, health=80, max_health=80, attack=20, defense=5, gold=50, inventory=[], player_class=player_class)
    elif class_choice == '3':
        player_class = "Rogue"
        player = Player(name, level=1, experience=0, health=90, max_health=90, attack=18, defense=6, gold=50, inventory=[], player_class=player_class)
    else:
        print("Invalid choice. Defaulting to Warrior.")
        player = Player(name, level=1, experience=0, health=100, max_health=100, attack=15, defense=8, gold=50, inventory=[], player_class="Warrior")

    return player

def create_enemy():
    enemy_data = {
        "Goblin": {"health": 30, "max_health": 30, "attack": 8, "defense": 3, "experience_reward": 20, "gold_reward": 10, "loot": ["Health Potion", "Dagger"]},
        "Skeleton": {"health": 40, "max_health": 40, "attack": 10, "defense": 5, "experience_reward": 30, "gold_reward": 15, "loot": ["Mana Potion", "Short Sword"]},
        "Orc": {"health": 50, "max_health": 50, "attack": 12, "defense": 7, "experience_reward": 40, "gold_reward": 20, "loot": ["Strength Elixir", "Battle Axe"]},
        "Dragon": {"health": 80, "max_health": 80, "attack": 18, "defense": 10, "experience_reward": 60, "gold_reward": 30, "loot": ["Fire Gem", "Dragon Scale"]}
    }

    enemy_name = random.choice(list(enemy_data.keys()))
    enemy_stats = enemy_data[enemy_name]
    return Enemy(enemy_name, **enemy_stats)

def create_quest():
    quest_data = {
        "Retrieve the Lost Sword": {"description": "Find the legendary sword hidden in the forest.", "reward_experience": 30, "reward_gold": 15},
        "Defeat the Bandit Leader": {"description": "Eliminate the notorious bandit leader in the mountains.", "reward_experience": 40, "reward_gold": 20},
        "Rescue the Villagers": {"description": "Save the kidnapped villagers from the evil sorcerer's tower.", "reward_experience": 50, "reward_gold": 25}
    }

    quest_name = random.choice(list(quest_data.keys()))
    quest_stats = quest_data[quest_name]
    return Quest(quest_name, **quest_stats)

def explore(player):
    print(f"{player.name}, you embark on a journey to explore the unknown...")

    while player.health > 0:
        enemy = create_enemy()
        print(f"\nUh-oh! You encounter a {enemy.name}!")

        while player.health > 0 and enemy.health > 0:
            print("\n--- Battle Menu ---")
            print("1. Attack")
            print("2. Defend")
            print("3. Use Item")
            print("4. Run away")

            choice = input("Enter your choice (1, 2, 3, or 4): ")

            if choice == '1':
                player_attack = player.attack + random.randint(-2, 2)
                enemy_defense = enemy.defense + random.randint(-1, 1)
                damage = max(0, player_attack - enemy_defense)
                enemy.health = max(0, enemy.health - damage)
                print(f"You attack the {enemy.name} and deal {damage} damage!")
            elif choice == '2':
                player_defense = player.defense + random.randint(-1, 1)
                print(f"You defend, increasing your defense for the next turn.")
            elif choice == '3':
                use_item(player)
            elif choice == '4':
                print("You attempt to run away.")
                if random.random() < 0.7:
                    print("You successfully escape!")
                    break
                else:
                    print("Escape failed! The enemy attacks you.")

            if enemy.health > 0:
                enemy_attack = enemy.attack + random.randint(-2, 2)
                player_defense = player.defense + random.randint(-1, 1)
                damage = max(0, enemy_attack - player_defense)
                player.health = max(0, player.health - damage)
                print(f"The {enemy.name} attacks you and deals {damage} damage!")

            print(f"\n{player.name}'s Health: {player.health}/{player.max_health} | {enemy.name}'s Health: {enemy.health}/{enemy.max_health}")

        if player.health > 0:
            player.experience += enemy.experience_reward
            player.gold += enemy.gold_reward
            player.inventory.extend(enemy.loot)
            player.display_stats()

            print(f"You defeated the {enemy.name} and gained {enemy.experience_reward} experience points!")
            print(f"You looted: {', '.join(enemy.loot)}")
            print(f"You earned {enemy.gold_reward} gold.")

            level_up(player)
            shop_menu(player)

            if random.random() < 0.3:
                quest = create_quest()
                print(f"\nYou discover a new quest: {quest.name}")
                print(f"{quest.description}")
                quest_menu(player, quest)

            print("\nDo you want to continue exploring?")
            explore_choice = input("Enter 'yes' or 'no': ")
            if explore_choice.lower() != 'yes':
                print("Thanks for playing!")
                break

        else:
            print("Game Over! You were defeated.")
            break

def use_item(player):
    if not player.inventory:
        print("Your inventory is empty.")
        return

    print("\n--- Inventory ---")
    for i, item in enumerate(player.inventory, 1):
        print(f"{i}. {item}")

    choice = input("Enter the number of the item to use (or enter '0' to go back): ")

    if choice.isdigit():
        choice = int(choice)
        if 0 < choice <= len(player.inventory):
            item_used = player.inventory.pop(choice - 1)
            if "Health Potion" in item_used:
                heal_amount = random.randint(10, 20)
                player.heal(heal_amount)
                print(f"You used a Health Potion and healed for {heal_amount} health.")
            elif "Mana Potion" in item_used:
                # You can add more effects for different items
                print("You used a Mana Potion.")
            else:
                print("You used the item.")
            player.display_stats()

def level_up(player):
    while player.experience >= player.level * 50:
        player.level += 1
        player.max_health += 20
        player.health = player.max_health
        player.attack += 5
        player.defense += 2
        print(f"\nCongratulations! You leveled up to Level {player.level}!")
        player.display_stats()

def shop_menu(player):
    print("\n--- Shop ---")
    print("1. Heal (Cost: 10 gold)")
    print("2. Buy Health Potion (Cost: 5 gold)")
    print("3. Buy Mana Potion (Cost: 5 gold)")
    print("4. Leave the shop")

    choice = input("Enter your choice (1, 2, 3, or 4): ")

    if choice == '1':
        if player.gold >= 10:
            player.gold -= 10
            player.heal(30)
            print("You paid 10 gold to heal.")
        else:
            print("You don't have enough gold to heal.")
    elif choice == '2':
        buy_item(player, "Health Potion", 5)
    elif choice == '3':
        buy_item(player, "Mana Potion", 5)
    elif choice == '4':
        print("You leave the shop.")

def buy_item(player, item, cost):
    if player.gold >= cost:
        player.gold -= cost
        player.inventory.append(item)
        print(f"You bought a {item} for {cost} gold.")
    else:
        print(f"You don't have enough gold to buy a {item}.")

def quest_menu(player, quest):
    print("\n--- Quest Menu ---")
    print(f"1. Accept Quest: {quest.name}")
    print("2. Decline Quest")

    choice = input("Enter your choice (1 or 2): ")

    if choice == '1':
        print(f"You accepted the quest: {quest.name}")
        print(f"{quest.description}")
        complete_quest(player, quest)
    elif choice == '2':
        print("You declined the quest.")

def complete_quest(player, quest):
    print(f"\n--- Quest Completed: {quest.name} ---")
    print(f"You earned {quest.reward_experience} experience points.")
    print(f"You received {quest.reward_gold} gold as a reward.")
    player.experience += quest.reward_experience
    player.gold += quest.reward_gold
    player.display_stats()

def main():
    player = create_character()
    explore(player)

if __name__ == "__main__":
    main()


