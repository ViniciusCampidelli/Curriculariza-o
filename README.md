class Estoque:
    def __init__(self):
        self.produtos = {}

    def adicionar_produto(self, nome, quantidade, preco):
        """Adiciona um novo produto ou atualiza a quantidade existente"""
        if nome in self.produtos:
            self.produtos[nome]['quantidade'] += quantidade
        else:
            self.produtos[nome] = {'quantidade': quantidade, 'preco': preco}
        print(f"{quantidade} unidades de '{nome}' foram adicionadas ao estoque.")

    def vender_produto(self, nome, quantidade):
        """Realiza a venda de um produto, decrementando a quantidade no estoque"""
        if nome not in self.produtos:
            print(f"Produto '{nome}' não encontrado no estoque.")
            return
        if self.produtos[nome]['quantidade'] < quantidade:
            print(f"Estoque insuficiente para '{nome}'. Disponível: {self.produtos[nome]['quantidade']} unidades.")
            return
        self.produtos[nome]['quantidade'] -= quantidade
        valor_total = quantidade * self.produtos[nome]['preco']
        print(f"Venda realizada: {quantidade} unidades de '{nome}' por R${valor_total:.2f}.")
        if self.produtos[nome]['quantidade'] == 0:
            print(f"Estoque de '{nome}' esgotado.")

    def visualizar_estoque(self):
        """Exibe o estoque atual com nome, quantidade e preço"""
        if not self.produtos:
            print("Estoque vazio.")
        else:
            print("\nEstoque atual:")
            for nome, dados in self.produtos.items():
                print(f"{nome}: {dados['quantidade']} unidades, R${dados['preco']:.2f} por unidade")

    def atualizar_preco(self, nome, novo_preco):
        """Atualiza o preço de um produto no estoque"""
        if nome in self.produtos:
            self.produtos[nome]['preco'] = novo_preco
            print(f"Preço de '{nome}' atualizado para R${novo_preco:.2f}.")
        else:
            print(f"Produto '{nome}' não encontrado no estoque.")
