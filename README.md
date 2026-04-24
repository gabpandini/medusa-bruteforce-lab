# Laboratório de Força Bruta com Kali Linux e Medusa

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Lab-green)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-blue)
![Medusa](https://img.shields.io/badge/Tool-Medusa-purple)
![DVWA](https://img.shields.io/badge/DVWA-orange)
![Metasploitable 2](https://img.shields.io/badge/Metasploitable2-red)

## 📌 Descrição

Este projeto tem como objetivo demonstrar, em ambiente controlado, a utilização da ferramenta **Medusa** no **Kali Linux** para simular ataques de força bruta em diferentes serviços vulneráveis.

Os testes foram realizados em máquinas virtuais configuradas no **VirtualBox**, utilizando:

- Kali Linux (máquina atacante)
- Metasploitable 2 (máquina vulnerável)
- DVWA (Damn Vulnerable Web Application)

O foco da atividade é compreender o funcionamento dos ataques de força bruta e identificar medidas de mitigação para prevenir esse tipo de vulnerabilidade.

---

## 🖥️ Ambiente Utilizado

| Máquina | Sistema | Função |
|--------|---------|--------|
| VM 1 | Kali Linux | Máquina atacante |
| VM 2 | Metasploitable 2 | Máquina vulnerável |
| Aplicação | DVWA | Aplicação web vulnerável |

### Configuração de Rede

As máquinas foram configuradas com:

- VirtualBox
- Adaptador **Host-Only**
- Comunicação interna entre VMs

Exemplo de IPs:

| Máquina | IP |
|--------|----|
| Kali | 192.168.56.102 |
| Metasploitable | 192.168.56.103 |

---

## 📂 Estrutura do Projeto

```bash
medusa-bruteforce-lab/
│── README.md
│── FTP.md
│── images/
```

---

## 🛡️ Medidas de Mitigação

As principais medidas recomendadas para evitar ataques de força bruta são:

#### 1. Senhas Fortes
- Utilizar senhas longas  
- Combinar letras maiúsulas e minúsculas, números e símbolos  
- Evitar senhas previsíveis  

#### 2. MFA
- Implementar autenticação multifator  

#### 3. Bloqueio Temporário
- Bloquear conta após várias tentativas falhas  

#### 4. Rate Limiting
- Limitar número de requisições por IP  

#### 5. Monitoramento
- Registrar tentativas suspeitas em logs  

#### 6. Restrição por IP
- Restringir acesso administrativo apenas a IPs confiáveis  
- Implementar regras de firewall para bloquear origens não autorizadas  
- Utilizar VPN para acesso a serviços sensíveis  

---

## 📚 Aprendizados Obtidos

Durante este laboratório foi possível compreender:

- Como funcionam ataques de força bruta  
- Diferença entre brute force e password spraying  
- Importância da enumeração prévia  
- Uso da ferramenta Medusa  
- Importância da prevenção em ambientes reais  

---

> [!IMPORTANT]
⚠️ Aviso: Este projeto foi realizado **exclusivamente em ambiente controlado para fins educacionais**.
O uso dessas técnicas em sistemas sem autorização é ilegal.

---

✨ *Projeto desenvolvido como parte de um desafio do bootcamp **Riachuelo - Cibersegurança** na **DIO**.*

