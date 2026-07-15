# **ODrive Commander v1.2**

![Interface do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/img/01.png)

A aplicação **ODrive Commander** é um utilitário para configurar, monitorar e controlar placas **ODrive | XDrive | Odesc** de forma intuitiva e em tempo real.

O seu principal objetivo é simplificar a preparação da ODrive | XDrive | Odesc para ser usada em projetos de **volantes Direct Drive com Force Feedback**, especialmente em conjunto com o firmware **OpenFFBoard**.

Esta aplicação é gratuita e **não possui qualquer vínculo com a ODrive Robotics**.

## **✅ Funcionalidades Principais**

* **Monitoramento:** Visualize em tempo real o status do eixo selecionado (com opção de alternar entre **axis0** ou **axis1**), **ID do dispositivo**, tensão do barramento, corrente Iq e torque estimado. **Novo:** Modo Overlay compacto para sobreposição e **registro do torque máximo** alcançado (com botão RST para reiniciar a leitura).  
* **Configuração Guiada:** Interface gráfica organizada por separadores para configurar facilmente os parâmetros de **Proteções** (incluindo limites de Corrente DC Positiva e Negativa), CAN, Motor e Encoder.  
* **Utilitários Essenciais:** Funções de um clique para ativar/desativar o eixo, **carregar firmware** (suporta arquivos .hex, .bin e .elf com opção de Full Erase), reiniciar a placa ou entrar em modo DFU.  
* **Gestão de Configurações:** Exporte as suas configurações para um arquivo JSON, importe configurações de um arquivo e salve as alterações permanentemente na memória da ODrive.  
* **Diagnóstico de Erros:** Uma tela dedicada para verificar e limpar erros da ODrive com um único clique.  
* **Console de Comandos Integrado:** Acesso direto à interface de comandos para usuários avançados, com histórico protegido e comando especial.  
* **Suporte Multilíngue:** Interface disponível em Português e Inglês, com a preferência do usuário a ser salva para futuras sessões.

## **🛠 Requisitos**

Para utilizar a aplicação, é necessário que:

* A placa **ODrive | XDrive | Odesc** esteja executando o [firmware 0.5.6](https://github.com/achavevirou/odrive_commander/tree/main/firmwares).  
* Os drivers da controladora no Windows estejam configurados corretamente (**usbser** e **WinUSB**).

## **🛠 Instalação dos Drivers com Zadig**

Para que o ODrive Commander se comunique perfeitamente com a placa, as duas interfaces da ODrive devem estar com os drivers corretos:

1. Baixe o Zadig: [https://zadig.akeo.ie](https://zadig.akeo.ie)
2. Abra o Zadig e vá em Options \> List All Devices.  
3. Na lista de dispositivos, selecione **ODrive 3.6 CDC Interface (Interface 0)**.  
4. Em Driver, verifique se o atual é o **usbser (USB Serial (CDC))**. Se não for, selecione-o e clique em Install Driver ou Reinstall Driver.  
5. Em seguida, volte à lista de dispositivos e selecione a **ODrive 3.6 Native Interface (Interface 2)**.  
6. Para esta interface, selecione obrigatoriamente o driver **WinUSB** e clique em Install Driver ou Reinstall Driver.

## **▶️ Usando a Aplicação**

1. Faça o download da última versão do **ODrive Commander** na página de Releases.
2. Execute a aplicação.  
3. Com a aplicação aberta, conecte a sua **ODrive | XDrive | Odesc** ao computador.  
4. Clique no botão **Conectar ODrive**. Se a placa for encontrada, o status mudará para "Conectado" e todos os campos serão preenchidos com os dados atuais da ODrive.

## **📖 Guia da Interface**

A interface está dividida em três áreas principais: o Painel de Controle à esquerda, o Painel de Monitoramento no topo direito e a Área de Configurações principal.

### **Painel de Monitoramento**

Assim que a conexão é estabelecida, esta área no canto superior direito é preenchida e atualizada, mostrando alguns dados da ODrive em tempo real. Conta com o botão RST para reiniciar a medição do pico de torque e a opção de ativar o Modo Overlay, ideal para visualizar a telemetria durante a pilotagem.

### **Painel de Controle (Esquerda)**

* **Idioma:** Permite alternar entre os idiomas disponíveis (PT-BR / EN-US). A sua escolha é salva e será carregada na próxima vez que abrir a aplicação.  
* **Status:** Mostra se a aplicação está "Conectada" ou "Desconectada".  
* **Conectar/Desconectar ODrive:** Inicia ou termina a comunicação com a placa.  
* **Reiniciar ODrive:** Envia um comando de reinicialização para a placa.  
* **Modo DFU:** Coloca a placa em modo DFU (STM32 BOOTLOADER) para carregamento de firmware.  
* **Proteções, CAN, Motor, Encoder:** Abre as respectivas páginas de configuração.  
* **Verificar Erros na ODrive:** Mostra a página de diagnóstico de erros.  
* **Console de Comandos:** Abre o console interativo.  
* **Ativar/Desativar Eixo:** Alterna o estado do motor entre "ativo" (em malha fechada) e "inativo/IDLE" (motor livre).  
* **Exportar Configuração:** Salva todos os parâmetros atuais da ODrive num arquivo .json.  
* **Carregar Configuração:** Carrega os parâmetros de um arquivo .json para a memória RAM da ODrive. **Atenção:** as configurações não são permanentes até serem salvas.  
* **Excluir Configuração:** Apaga a configuração guardada na memória permanente da ODrive e reinicia a placa.

### **Páginas de Configuração**

Cada página permite alterar um grupo de parâmetros. Após fazer as suas alterações, clique no botão **"Aplicar"** para enviar os novos valores a ODrive.

**Importante:** Clicar em "Aplicar" apenas altera os valores na memória RAM. Para tornar as alterações permanentes, é necessário clicar no botão **"Salvar Configurações"**.

---

Acesse a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md) para obter explicações detalhadas sobre cada parâmetro e aba da aplicação.

## **🙏 Um Pedido**

Se a aplicação ODrive Commander foi útil para você, considere **inscrever-se no canal**:

🔗 [Canal A Chave Virou no YouTube](https://www.youtube.com/@achavevirou)

## **🌐 Outros Links**

* 📸 [Instagram A Chave Virou](https://www.instagram.com/achavevirou)  
* 📘 [Facebook A Chave Virou](https://www.facebook.com/share/g/1ArMr9tooj/?mibextid=wwXIfr)  
* 🐙 [GitHub A Chave Virou](https://www.google.com/search?q=https://github.com/achavevirou)
* 💳 [Doar via PayPal](https://www.paypal.com/donate/?hosted_button_id=NVHGDWED34A26)
