import os
import matplotlib.pyplot as plt
import pandas as pd

estoque = []
id_contador = 1

# Commit 1: Implementa funções de cadastro e exclusão de produtos no estoque
def cadastrar_produto():
    """Permite ao usuário cadastrar um novo produto."""
    global id_contador
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Cadastrar Novo Produto \n")
    nome = input("Nome do produto: ").strip().capitalize()
    categoria = input("Categoria: ").strip().capitalize()

    while True:
        try:
            preco = float(input("Preço: "))
            if preco <= 0:
                print("O preço deve ser maior que zero. Tente novamente.")
            else:
                break
        except ValueError:
            print("Entrada inválida. Por favor, digite um número para o preço.")

    while True:
        try:
            quantidade = int(input("Quantidade inicial: "))
            if quantidade < 0:
                print("A quantidade não pode ser negativa. Tente novamente.")
            else:
                break
        except ValueError:
            print("Entrada inválida. Por favor, digite um número inteiro para a quantidade.")

    novo_produto = {
        "id": id_contador,
        "nome": nome,
        "categoria": categoria,
        "preco": preco,
        "quantidade": quantidade
    }
    estoque.append(novo_produto)
    id_contador += 1
    print("\nProduto cadastrado com sucesso!")
    input("\nPressione Enter para continuar...")

def excluir_produto():
    """Permite ao usuário excluir um produto pelo ID."""
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Excluir Produto \n")

    if not estoque:
        print("Nenhum produto cadastrado para excluir.")
        input("\nPressione Enter para continuar...")
        return
