Não é tão simples quanto apenas colocar o IP, mas é possível! Você precisa configurar algumas coisas no seu Ubuntu. Segue o passo a passo:

## 1. Configurar o MySQL no Ubuntu

### Editar o arquivo de configuração do MySQL:
```bash
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

### Encontrar a linha:
```
bind-address = 127.0.0.1
```
### E alterar para:
```
bind-address = 0.0.0.0
```
(Isto permite conexões de qualquer IP)

## 2. Criar usuário para acesso remoto

Conecte ao MySQL no Ubuntu:
```bash
mysql -u root -p
```

### Criar usuário (substitua 'senha' por uma senha segura):
```sql
CREATE USER 'usuario_remoto'@'%' IDENTIFIED BY 'sua_senha_segura';
GRANT ALL PRIVILEGES ON *.* TO 'usuario_remoto'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

## 3. Configurar Firewall

```bash
sudo ufw allow 3306
```

## 4. Reiniciar o MySQL
```bash
sudo systemctl restart mysql
```

## 5. No Windows

Agora no seu SGBD MySQL no Windows (como MySQL Workbench, HeidiSQL, etc):
- **Host/IP**: IP do notebook Ubuntu
- **Port**: 3306
- **Username**: usuario_remoto
- **Password**: sua_senha_segura

## ⚠️ Importante para Segurança:

1. **Use senhas fortes**
2. **Considere restringir o acesso por IP** (em vez de `%` usar IP específico do Windows)
3. **Em redes públicas, use VPN ou SSH tunneling**

## Alternativa mais segura: SSH Tunnel

Se estiver em rede não confiável, use Putty no Windows para criar túnel SSH:
- Host: IP do Ubuntu
- Port: 22
- Em SSH > Tunnel: Source 3306, Destination localhost:3306

Depois conecte no SGBD usando `localhost:3306`

Quer que eu detalhe alguma parte específica?
