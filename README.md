frog_leap_game.py: This file will contain the Python script for the Frog Leap puzzle game.

python
Copy code
# frog_leap_game.py

def display_positions(positions):
    indices = list(range(len(positions)))
    print(f"{indices}")
    print(positions)

def check_winning_condition(positions):
    return positions == ['B', 'B', 'B', '-', 'G', 'G', 'G']

def main():
    # Initial positions list
    positions = ['G', 'G', 'G', '-', 'B', 'B', 'B']
    
    # Infinite loop
    while True:
        # Display the current state
        display_positions(positions)

        # Check for winning condition
        if check_winning_condition(positions):
            print("You Win!")
            break

        # Ask the user for input
        user_input = input("Press 'q' to quit, else enter the position of the piece: ")

        if user_input.lower() == 'q':
            print("You Lose. Quitting the game.")
            break
        else:
            try:
                selected_position = int(user_input)
                if 0 <= selected_position <= 6 and positions[selected_position] == 'G':
                    current_position = selected_position
                    # Check condition 1
                    if current_position + 1 <= 6 and positions[current_position + 1] == '-':
                        pos2 = current_position + 1
                        print(f"Valid move. Empty leaf at position {pos2}")
                        # Swap the elements in the list
                        positions[current_position], positions[pos2] = positions[pos2], positions[current_position]
                    # Check condition 2
                    elif current_position + 2 <= 6 and positions[current_position + 2] == '-' and positions[current_position + 1] == 'B':
                        pos2 = current_position + 2
                        print(f"Valid move. Empty leaf at position {pos2}")
                        # Swap the elements in the list
                        positions[current_position], positions[pos2] = positions[pos2], positions[current_position]
                    # Check condition 3
                    else:
                        print("Invalid move.")
                        continue  # Skip the remaining part of the iteration
                elif 0 <= selected_position <= 6 and positions[selected_position] == 'B':
                    current_position = selected_position
                    # Check condition 1
                    if current_position - 1 >= 0 and positions[current_position - 1] == '-':
                        pos2 = current_position - 1
                        print(f"Valid move. Empty leaf at position {pos2}")
                        # Swap the elements in the list
                        positions[current_position], positions[pos2] = positions[pos2], positions[current_position]
                    # Check condition 2
                    elif current_position - 2 >= 0 and positions[current_position - 2] == '-' and positions[current_position - 1] == 'G':
                        pos2 = current_position - 2
                        print(f"Valid move. Empty leaf at position {pos2}")
                        # Swap the elements in the list
                        positions[current_position], positions[pos2] = positions[pos2], positions[current_position]
                    # Check condition 3
                    else:
                        print("Invalid move.")
                        continue  # Skip the remaining part of the iteration
                else:
                    print("Invalid move. Please enter a valid position for 'G' or 'B'.")
            except ValueError:
                print("Invalid input. Please enter a valid position or 'q' to quit.")

if __name__ == "__main__":
    main()
README.md: This file will contain a brief explanation of the game and instructions on how to play.

# Frog Leap Puzzle Game

This is a simple Python implementation of the Frog Leap puzzle game.

display_positions Function: This function takes a list of positions as input and prints the indices and the elements of the list to display the current state of the game.

check_winning_condition Function: This function checks if the winning condition is met. The winning condition is when all the frogs are arranged in the order 'B', 'B', 'B', '-', 'G', 'G', 'G'.

main Function: This is the main function that runs the game. It contains an infinite loop to keep the game running until the player quits or wins. It checks for the winning condition, takes user input, and makes moves based on the conditions specified in the game rules.

Game Rules:

Frogs labeled 'G' can only move to the right.
Frogs labeled 'B' can only move to the left.
Frogs can jump over an adjacent frog to an empty leaf.
User Input:

The player can input the position of the frog they want to move.
Pressing 'q' will quit the game.
Valid Moves:

Valid moves are determined based on the rules mentioned above.
If a move is valid, the game state is updated by swapping the positions of the frogs.
Winning Condition:

The game checks for the winning condition after each move.
If the winning condition is met, the game displays "You Win!" and exits.
Error Handling:

The script handles invalid inputs gracefully, such as non-integer inputs or positions that are out of bounds.
## How to Play

- Run the `frog_leap_game.py` script in your Python environment.
- Follow the on-screen instructions to input the position of the frog you want to move.
- Press 'q' to quit the game.
- The goal is to move all the frogs to the right, following the rules of the game.

Have fun playing!

## Rules

- Frogs labeled 'G' can only move to the right.
- Frogs labeled 'B' can only move to the left.
- Frogs can jump over an adjacent frog to an empty leaf.
- The game is won when all the frogs are arranged in the order 'B', 'B', 'B', '-', 'G', 'G', 'G'.



Once you have these files, you can create a new repository on GitHub, add these files, and commit them to the repository. Users can then clone the repository to play the game on their local machines.
