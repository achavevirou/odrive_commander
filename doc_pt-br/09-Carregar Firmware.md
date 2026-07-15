**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Carregar Firmware**

A aba "Carregar Firmware" permite atualizar o firmware da sua placa de forma intuitiva, utilizando o protocolo DFU (Device Firmware Upgrade). A aplicação oferece suporte a arquivos nos formatos `.hex`, `.bin` e `.elf`.

### **Como realizar a atualização**

1. **Modo DFU:** Antes de tudo, a sua placa deve estar em modo DFU. Você pode utilizar o botão "Modo DFU" no Painel de Controle à esquerda para colocar a placa automaticamente neste estado.
2. **Selecionar Arquivo:** Clique no botão **"Selecionar Firmware..."** e escolha o arquivo do firmware que deseja gravar.
3. **Opção Full Erase:** 
   * **Executar Full Erase antes de gravar:** Se marcada, a aplicação apagará completamente toda a memória flash do microcontrolador, incluindo configurações salvas e calibrações, antes de gravar o novo arquivo.
   * **⚠️ Atenção:** Esta é uma operação destrutiva. Utilize apenas se necessário (ex: ao atualizar para uma versão de firmware com mudanças estruturais profundas ou caso a placa esteja apresentando comportamentos anômalos persistentes).
4. **Gravar:** Clique no botão **"Gravar Firmware"**. A barra de progresso indicará o status da transferência e gravação.

### **Comportamento durante a gravação**

* **Status:** A etiqueta abaixo da barra de progresso informará em tempo real o que está acontecendo (ex: "Apagando memória flash", "Gravando firmware", "Verificando").
* **Finalização:** Após a conclusão bem-sucedida, o firmware será verificado e a placa será reiniciada automaticamente para iniciar o novo firmware.

### **Solução de Problemas**

* **Dispositivo não encontrado:** Se a gravação falhar com um erro indicando que nenhum dispositivo DFU foi encontrado, certifique-se de que a placa está realmente em modo DFU (geralmente indicado por um comportamento diferente nos LEDs da placa ou pelo reconhecimento do dispositivo como "STM32 BOOTLOADER" no Gerenciador de Dispositivos do Windows).
* **Driver DFU:** Certifique-se de que o driver do dispositivo está corretamente instalado para permitir o acesso via `dfu-util`.

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).