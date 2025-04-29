# Azure Virtual Machine - Configuração e Redimensionamento

Este projeto é um resumo prático sobre como criar, configurar e redimensionar Máquinas Virtuais (VMs) no Microsoft Azure. O objetivo é ajudar iniciantes a entenderem como realizar essas operações no Azure, tanto pelo portal web quanto utilizando a linha de comando (Azure CLI). Aprendi esses conceitos durante o curso na plataforma **Digital Innovation One (DIO)**, que proporcionou uma excelente base para trabalhar com infraestrutura de nuvem.
---
## Introdução

Este projeto visa consolidar o aprendizado de como configurar e redimensionar máquinas virtuais no Azure, além da criação e dimensionamento de áreas de trabalho no Azure. O guia está dividido entre instruções do portal Azure e uso da linha de comando (Azure CLI), e reflete o conhecimento adquirido nos cursos da DIO.

## Criando uma Máquina Virtual no Azure

1. **Acesse o portal**
   - Entre no portal do Azure: [https://portal.azure.com](https://portal.azure.com)

2. **Criação da Máquina Virtual**
   - No menu lateral, clique em "Máquinas Virtuais" > "+ Criar" > "Máquina Virtual".
   - Preencha os seguintes detalhes:
     - **Assinatura**: Escolha sua assinatura ativa.
     - **Grupo de Recursos**: Selecione ou crie um novo.
     - **Nome da VM**: Exemplo: `vm-teste-lucas`.
     - **Região**: Escolha a região mais próxima (exemplo: "Brasil Sul").
     - **Imagem**: Selecione o sistema operacional (exemplo: "Ubuntu 22.04 LTS" ou "Windows Server 2022").
     - **Tamanho da VM**: Escolha conforme sua necessidade, como `Standard_B2s`.
     - **Autenticação**:
       - Para Linux: chave SSH ou usuário e senha.
       - Para Windows: usuário e senha.
     - **Disco do sistema operacional**: SSD padrão.

3. **Configuração de Rede**
   - Habilite IP público e libere as portas necessárias (porta 22 para Linux, 3389 para Windows).
   
4. **Revisar e Criar**
   - Confira as configurações e clique em "Criar".

## Redimensionando uma Máquina Virtual

1. **Acesse sua VM**
   - No portal Azure, vá em "Máquinas Virtuais" e selecione a VM que deseja alterar.

2. **Redimensionar a VM**
   - No menu da VM, clique em "Tamanho".
   - Selecione o novo modelo de VM (SKU) e clique em "Redimensionar".
   - **Observação**: Algumas mudanças exigem que a VM seja desligada temporariamente.

## Usando Azure CLI

### Criando uma VM via linha de comando

```bash
az login

az vm create \
  --resource-group MeuGrupoDeRecursos \
  --name MinhaVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
