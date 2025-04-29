# Azure Virtual Machine - Configuração e Redimensionamento

## Introdução

Este projeto é um resumo prático do que aprendi durante meus estudos na plataforma Digital Innovation One (DIO).

No curso, explorei os principais conceitos sobre como criar, configurar e redimensionar Máquinas Virtuais (VMs) no Microsoft Azure, um dos principais serviços de nuvem do mercado.  
Aqui, organizei os passos e comandos que pratiquei, como uma forma de consolidar o aprendizado e também compartilhar o conhecimento com outras pessoas que estejam começando na área de computação em nuvem.

A proposta deste projeto é mostrar, de forma simples, como realizar essas operações no Azure, tanto pelo portal web quanto utilizando a linha de comando (Azure CLI).

---

## Como criar uma Máquina Virtual no Azure

### 1. Acesse o portal
Entre no site: [https://portal.azure.com](https://portal.azure.com)

### 2. Vá até a área de Máquinas Virtuais
No menu lateral, clique em "Máquinas Virtuais" e depois em "+ Criar" > "Máquina Virtual".

### 3. Configure os detalhes básicos
- **Assinatura**: Escolha sua assinatura ativa.
- **Grupo de Recursos**: Selecione um existente ou crie um novo.
- **Nome da VM**: Exemplo: `vm-teste-lucas`.
- **Região**: Escolha uma região próxima, como "Brasil Sul".
- **Imagem**: Escolha o sistema operacional, como "Ubuntu 22.04 LTS" ou "Windows Server 2022".
- **Tamanho da VM**: Defina conforme sua necessidade, por exemplo: `Standard_B2s`.
- **Autenticação**:
  - Para Linux: pode usar chave SSH ou usuário e senha.
  - Para Windows: apenas usuário e senha.
- **Disco do sistema operacional**: Pode usar o SSD padrão.

### 4. Configuração de rede
- Habilite IP público.
- Libere as portas necessárias:
  - Linux: porta 22 (SSH)
  - Windows: porta 3389 (RDP)

### 5. Revisar e criar
Confira todas as informações e clique em "Criar".

---

## Como redimensionar uma Máquina Virtual

### 1. Acesse sua VM
No portal Azure, vá até "Máquinas Virtuais" e selecione a VM que deseja alterar.

### 2. Alterar o tamanho
- No menu da VM, clique em "Tamanho".
- Escolha o novo modelo (SKU) de VM.
- Clique em "Redimensionar".

Obs: Algumas mudanças exigem desligar a máquina temporariamente.

---

## Recomendações

- Antes de redimensionar ou fazer mudanças importantes, é recomendável criar um snapshot da VM.
- Para acompanhar o desempenho, utilize o Azure Monitor.
- Lembre-se de verificar o custo do novo tamanho antes de aplicar as mudanças.

---

## Usando Azure CLI (linha de comando)

### Criar uma VM pelo terminal

```bash
az login

az vm create \
  --resource-group MeuGrupoDeRecursos \
  --name MinhaVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
