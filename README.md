

# **ODrive Commander v1.0**

A aplicação **ODrive Commander** é um utilitário para configurar, monitorar e controlar placas **ODrive | XDrive | Odesc** de forma intuitiva e em tempo real.

O seu principal objetivo é simplificar a preparação da ODrive | XDrive | Odesc para ser usada em projetos de **volantes Direct Drive com Force Feedback**, especialmente em conjunto com o firmware **OpenFFBoard**.

Esta aplicação é gratuita e **não possui qualquer vínculo com a ODrive Robotics**.

## **✅ Funcionalidades Principais**

* **Monitoramento:** Visualize em tempo real o status do eixo, tensão do barramento, correntes de fase, corrente Iq e torque estimado.  
* **Configuração Guiada:** Interface gráfica organizada por separadores para configurar facilmente os parâmetros do Resistor, CAN, Motor e Encoder.  
* **Utilitários Essenciais:** Funções de um clique para ativar/desativar o eixo, reiniciar a placa ou entrar em modo DFU.  
* **Gestão de Configurações:** Exporte as suas configurações para um arquivo JSON, importe configurações de um arquivo e salve as alterações permanentemente na memória da ODrive.  
* **Diagnóstico de Erros:** Uma tela dedicada para verificar e limpar erros da ODrive com um único clique.  
* **Console de Comandos Integrado:** Acesso direto à interface de comandos para usuários avançados, com histórico protegido e comando especial.  
* **Suporte Multilíngue:** Interface disponível em Português e Inglês, com a preferência do usuário a ser salva para futuras sessões.

## **🛠 Requisitos**

Para utilizar a aplicação, é necessário que:

* A placa **ODrive | XDrive | Odesc** esteja executando o **firmware 0.5.6**.  
* O driver da controladora no Windows seja o **WinUSB**.

## **🛠 Instalação do Driver com Zadig**

1. Baixe o Zadig: [https://zadig.akeo.ie](https://zadig.akeo.ie)  
2. Abra o Zadig e vá em Options \> List All Devices.  
3. Na lista de dispositivos, selecione ODrive 3.6 CDC Interface (Interface 0).  
4. Em Driver, verifique se o atual é WinUSB.  
5. Se não for, selecione WinUSB e clique em Install Driver ou Reinstall Driver.  
6. Repita para o dispositivo ODrive 3.6 Native Interface (Interface 2).

## **▶️ Usando a Aplicação**

1. Faça o download da última versão do **ODrive Commander** na página de [Releases](https://github.com/achavevirou/odrive_commander/releases).
2. Execute a aplicação.  
3. Com a aplicação aberta, conecte a sua **ODrive | XDrive | Odesc** ao computador.  
4. Clique no botão **Conectar ODrive**. Se a placa for encontrada, o status mudará para "Conectado" e todos os campos serão preenchidos com os dados atuais da ODrive.

## **📖 Guia da Interface**

A interface está dividida em três áreas principais: o Painel de Controle à esquerda, o Painel de Monitoramento no topo direito e a Área de Configurações principal.

### **Painel de Monitoramento**

Assim que a conexão é estabelecida, esta área no canto superior direito é preenchida e atualizada, mostrando alguns dados da ODrive em tempo real.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/01.png)

### **Painel de Controle (Esquerda)**

* **Idioma:** Permite alternar entre os idiomas disponíveis (PT-BR / EN-US). A sua escolha é salva e será carregada na próxima vez que abrir a aplicação.  
* **Status:** Mostra se a aplicação está "Conectada" ou "Desconectada".  
* **Conectar/Desconectar ODrive:** Inicia ou termina a comunicação com a placa.  
* **Reiniciar ODrive:** Envia um comando de reinicialização para a placa.  
* **Modo DFU:** Coloca a placa em modo DFU (STM32 BOOTLOADER) para carregamento de firmware.  
* **Resistor, CAN, Motor, Encoder:** Abre as respectivas páginas de configuração.  
* **Verificar Erros na ODrive:** Mostra a página de diagnóstico de erros.  
* **Console de Comandos:** Abre o console interativo.  
* **Ativar/Desativar Eixo:** Alterna o estado do motor entre "ativo" (em malha fechada) e "inativo/IDLE" (motor livre).  
* **Exportar Configuração:** Salva todos os parâmetros atuais da ODrive num arquivo .json.  
* **Carregar Configuração:** Carrega os parâmetros de um arquivo .json para a memória RAM da ODrive. **Atenção:** as configurações não são permanentes até serem salvas.  
* **Excluir Configuração:** Apaga a configuração guardada na memória permanente da ODrive e reinicia a placa.

### **Páginas de Configuração**

Cada página permite alterar um grupo de parâmetros. Após fazer as suas alterações, clique no botão **"Aplicar"** para enviar os novos valores a ODrive.

**Importante:** Clicar em "Aplicar" apenas altera os valores na memória RAM. Para tornar as alterações permanentes, é necessário clicar no botão **"Salvar Configurações"**.

#### **Página do Resistor**

Configura os parâmetros do resistor de frenagem, essencial para proteger a ODrive de picos de tensão regenerativa.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/02.png)

#### **Página da CAN**

Define o ID e a velocidade da comunicação CAN.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/03.png)

#### **Página do Motor**

Aqui pode configurar os parâmetros fundamentais do seu motor, como o número de pares de polos, constante de torque, limites de corrente e proteções.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/04.png)

#### **Página do Encoder**

Esta página agrupa todas as configurações relacionadas com o encoder, incluindo o CPR, o uso do Índice Z e as flags de inicialização. Além disso, nessa página é feita a calibração do motor e encoder.

* **Calibração Completa do Eixo:** Inicia a rotina de calibração completa do motor e do encoder.  
* **Motor/Encoder Pré Calibrado:** Estas opções informam à ODrive para pular as respectivas rotinas de calibração na inicialização.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/05.png)

#### **Página de Verificação de Erros**

Exibe os erros ativos na ODrive e permite limpá-los.

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/06.png)

### **Console de Comandos**

Para usuários avançados, o console permite enviar qualquer comando que seja válido para o odrivetool.

* **Comandos Padrão:** dev0.vbus\_voltage, dev0.axis0.motor.config.current\_lim \= 50, etc.  
* **Comando Especial:** dev0.axis0.current.estimate(valor\_max\_torque)  
  * Este comando utiliza a constante de torque configurada na ODrive para gerar uma tabela de estimativa da corrente Iq necessária para atingir cada nível de torque, desde 1 Nm até ao valor\_max\_torque (limitado a 40).

![enter image description here](https://github.com/achavevirou/odrive_commander/blob/main/img/07.png)

Acesse a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).

## **🙏 Um Pedido**

Se a aplicação ODrive Commander foi útil para você, considere **inscrever-se no canal**:

🔗 [Canal A Chave Virou no YouTube](https://www.youtube.com/@achavevirou)

## **🌐 Outros Links**

* 📸 [Instagram A Chave Virou](https://www.instagram.com/achavevirou)  
* 📘 [Facebook A Chave Virou](https://www.facebook.com/share/g/1ArMr9tooj/?mibextid=wwXIfr)  
* 🐙 [GitHub A Chave Virou](https://www.google.com/search?q=https://github.com/achavevirou)
* 💳 [Doar via PayPal](https://www.paypal.com/donate/?hosted_button_id=NVHGDWED34A26)
