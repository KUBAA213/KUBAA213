import random
import time

class Game:
    def __init__(self):
        self.locations = ["las", "miasto", "pustynia", "góry", "rzeka"]
        self.actions = ["ukryć się", "biec dalej", "walczyć", "wziąć skrót"]
        self.game_over = False
        self.distance = 0

    def start_game(self):
        print("Witaj w grze! Jesteś podróżnikiem, który ucieka przed policją.")
        time.sleep(2)
        print("Twoim celem jest uciec jak najdalej.")
        time.sleep(2)
        while not self.game_over:
            self.next_move()

    def next_move(self):
        location = random.choice(self.locations)
        action = random.choice(self.actions)
        print(f"\nZnajdujesz się w: {location}. Co chcesz zrobić?")
        for idx, act in enumerate(self.actions, 1):
            print(f"{idx}. {act}")

        choice = int(input("\nWybierz numer akcji: "))
        if self.actions[choice - 1] == action:
            print(f"Dobra decyzja! {action.capitalize()} pozwoliło ci uciec dalej.")
            self.distance += random.randint(1, 10)
        else:
            print(f"Zły wybór! {action.capitalize()} sprawiło, że policja cię dogoniła.")
            self.game_over = True

        time.sleep(2)
        print(f"Przebyty dystans: {self.distance} km")

        if not self.game_over:
            continue_game = input("Czy chcesz kontynuować ucieczkę? (tak/nie): ")
            if continue_game.lower() != "tak":
                self.game_over = True
                print(f"Gra zakończona. Przebyty dystans: {self.distance} km")

if __name__ == "__main__":
    game = Game()
    game.start_game()
