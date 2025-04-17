Sim, exatamente! A principal diferença é que, **sem o MySQL Workbench**, você vai gerenciar o MySQL **diretamente pelo terminal** (via linha de comando). Isso não é um problema — muitos administradores de bancos de dados preferem o terminal por ser mais rápido e flexível.  

Aqui está um guia prático para você trabalhar só com o terminal:

---

### **1. Acessando o MySQL pelo Terminal**
Para conectar-se como **root** (substitua `sua_senha` pela senha que você definiu no `mysql_secure_installation`):
```bash
mysql -u root -p
```
- Digite a senha quando solicitado.

---

### **2. Comandos Essenciais no Terminal**
#### **Gerenciar Bancos de Dados**
- **Listar todos os bancos de dados**:
  ```sql
  SHOW DATABASES;
  ```
- **Criar um novo banco de dados**:
  ```sql
  CREATE DATABASE nome_do_banco;
  ```
- **Deletar um banco de dados**:
  ```sql
  DROP DATABASE nome_do_banco;
  ```

#### **Gerenciar Usuários e Permissões**
- **Criar um novo usuário**:
  ```sql
  CREATE USER 'novo_usuario'@'localhost' IDENTIFIED BY 'senha_segura';
  ```
- **Conceder todos os privilégios a um usuário**:
  ```sql
  GRANT ALL PRIVILEGES ON nome_do_banco.* TO 'novo_usuario'@'localhost';
  FLUSH PRIVILEGES;  -- Atualiza as permissões
  ```
- **Revogar privilégios**:
  ```sql
  REVOKE ALL PRIVILEGES ON nome_do_banco.* FROM 'usuario'@'localhost';
  ```

#### **Trabalhar com Tabelas**
- **Selecionar um banco de dados**:
  ```sql
  USE nome_do_banco;
  ```
- **Listar tabelas**:
  ```sql
  SHOW TABLES;
  ```
- **Criar uma tabela**:
  ```sql
  CREATE TABLE clientes (
      id INT AUTO_INCREMENT PRIMARY KEY,
      nome VARCHAR(50),
      email VARCHAR(100)
  );
  ```
- **Inserir dados**:
  ```sql
  INSERT INTO clientes (nome, email) VALUES ('João', 'joao@exemplo.com');
  ```

---

### **3. Exportar/Importar Bancos de Dados (Backup)**
#### **Exportar (backup)**
```bash
mysqldump -u root -p nome_do_banco > backup.sql
```

#### **Importar (restaurar)**
```bash
mysql -u root -p nome_do_banco < backup.sql
```

---

### **4. Dicas para Facilitar no Terminal**
- **Auto-complete**: Pressione `Tab` para completar nomes de bancos/tabelas.
- **Histórico de comandos**: Use as teclas `↑` e `↓` para navegar entre comandos recentes.
- **Sair do MySQL**: Digite `EXIT` ou `Ctrl + D`.

---

### **5. Alternativas ao Workbench (Se Quiser Interface)**
Se eventualmente sentir falta de uma interface gráfica:
- **Instale o `DBeaver`** (grátis e multiplataforma):
  ```bash
  sudo snap install dbeaver-ce
  ```
- **Ou use o `Adminer`** (leve e baseado na web):
  ```bash
  sudo apt install adminer
  ```

---

### **Resumo**
- **Você pode fazer TUDO pelo terminal** — desde criar bancos até gerenciar usuários.  
- **É mais rápido e direto** que interfaces gráficas, uma vez que você se acostumar.  
- **Backups e operações complexas** são facilmente automatizáveis via terminal.  

Se precisar de exemplos específicos ou encontrar dificuldades, é só perguntar!
