# Lista de compras inicial
shopping_list = []

def show_menu():
    print("\nMenu:")
    print("1. Adicionar item")
    print("2. Visualizar lista")
    print("3. Remover item")
    print("4. Salvar lista")
    print("5. Sair")

def add_item():
    item = input("Digite o item para adicionar: ")
    shopping_list.append(item)
    print(f"'{item}' foi adicionado à lista.")

def view_items():
    if shopping_list:
        print("\nItens na lista:")
        for i, item in enumerate(shopping_list, 1):
            print(f"{i}. {item}")
    else:
        print("\nA lista está vazia.")

def remove_item():
    view_items()
    if shopping_list:
        try:
            index = int(input("Digite o número do item para remover: ")) - 1
            removed_item = shopping_list.pop(index)
            print(f"'{removed_item}' foi removido da lista.")
        except (ValueError, IndexError):
            print("Opção inválida. Tente novamente.")

def save_list():
    with open("shopping_list.txt", "w") as file:
        for item in shopping_list:
            file.write(item + "\n")
    print("Lista salva em 'shopping_list.txt'.")

# Loop principal
while True:
    show_menu()
    choice = input("Escolha uma opção: ")

    if choice == "1":
        add_item()
    elif choice == "2":
        view_items()
    elif choice == "3":
        remove_item()
    elif choice == "4":
        save_list()
    elif choice == "5":
        print("Saindo do programa. Até logo!")
        break
    else:
        print("Opção inválida. Tente novamente.")
