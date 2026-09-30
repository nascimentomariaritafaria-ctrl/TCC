import sqlite3

def conectar():
    conexao = sqlite3.connect("database.db")

    conexao.row_factory = sqlite3.Row

    cursor = conexao.cursor()

    return conexao

def criar_tarefa():
    conexao = conectar()
    cursor = conexao.cursor()

    cursor.execute(""" 
    CREATE TABLE IF NOT EXISTS usuarios (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE,
    senha TEXT NOT NULL
    )
    
    
    """)

    conexao.commit()
    conexao.close()

if __name__ == '__main__':
    conectar()
    print("Banco inicializado com sucesso! ")
