**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Painel de Controle e Monitoramento**

A interface principal do ODrive Commander está dividida em duas áreas sempre visíveis: o **Painel de Controle** à esquerda, onde todas as ações são iniciadas, e o **Painel de Monitoramento** no topo à direita, que exibe os dados vitais da ODrive em tempo real.

## **Painel de Controle (Esquerda)**

Este painel contém todos os botões e seletores fundamentais para interagir com a aplicação e com a placa.

### **1. Conexão e Status**

* **Idioma:** Permite alternar a linguagem da interface entre Português (PT-BR) e Inglês (EN-US). A sua escolha é salva automaticamente e será lembrada na próxima vez que abrir a aplicação.
* **Eixo:** Seleciona qual eixo da controladora (**axis0** ou **axis1**) será lido no monitoramento e receberá as configurações das abas ao lado.
* **Status:** Indica o estado atual da conexão.
  * **Desconectado:** Não há ODrive conectada com a aplicação.
  * **Conectando...:** A aplicação está procurando por uma ODrive conectada via USB.
  * **Conectado:** A comunicação com a ODrive foi estabelecida com sucesso.
* **Dispositivo:** Exibe o ID único de hardware (em formato hexadecimal) da placa conectada.
* **Conectar/Desconectar ODrive:** O botão principal para iniciar ou terminar a comunicação com a placa.
* **Reiniciar ODrive:** Envia um comando de reinicialização de software para a ODrive.
* **Modo DFU:** Coloca a ODrive em modo DFU (STM32 BOOTLOADER) para permitir a gravação de um novo firmware.

### **2. Navegação de Configurações**

Este grupo de botões funciona como o menu principal. Clicar num botão abre a página correspondente na área central da janela. O botão da página atualmente selecionada fica destacado com outra cor.

* **Proteções, CAN, Motor, Encoder:** Abre as respectivas páginas de configuração para o eixo selecionado.
* **Verificar Erros na ODrive:** Abre uma tela que exibe os erros atuais reportados pelo sistema ou pelo eixo e permite limpá-los.
* **Console de Comandos:** Abre o console interativo para o envio direto de comandos Python para a placa.

### **3. Utilitários**

Este grupo oferece acesso rápido a funções cruciais de gestão e operação.

* **Ativar/Desativar Eixo:** Alterna o estado do motor entre "ativo" (em malha fechada/CLOSED_LOOP_CONTROL) e "inativo/IDLE" (motor livre).
* **Exportar Configuração:** Abre uma janela para salvar todos os parâmetros atuais da ODrive num arquivo de texto (.json). É ideal para fazer backups.
* **Carregar Configuração:** Carrega os parâmetros de um arquivo .json diretamente para a memória RAM da ODrive. **Atenção:** As configurações carregadas só se tornam permanentes após clicar em "Salvar Configurações".
* **Excluir Configuração:** Apaga permanentemente toda a configuração salva na memória da ODrive, revertendo-a para os padrões de fábrica, e reinicia a placa. **Use com extrema cautela!**
* **Carregar Firmware:** Abre a interface dedicada para carregar o firmware da controladora usando arquivos .bin, .hex ou .elf.

## **Painel de Monitoramento**

Assim que a conexão é estabelecida, este painel é preenchido com dados lidos diretamente do eixo selecionado na ODrive e atualizados múltiplas vezes por segundo.

### **Ferramentas de Exibição**
* **Modo Overlay:** Quando ativado, oculta as abas laterais e inferiores, transformando a interface num pequeno painel sem bordas que fica "preso" sempre no topo (Always on Top). É perfeito para monitorar a telemetria enquanto o simulador roda em modo Janela Sem Bordas (Borderless) ou Windowed.
* **Slider de Opacidade:** Fica ativo apenas durante o Modo Overlay, permitindo deixar o painel transparente para não obstruir a visão da pista.
* **RST (Reset):** Um botão rápido para zerar a medição travada no "Torque (Máx.)".

### **Dados de Telemetria**
* **Status da ODrive:** Mostra o estado de operação atual do eixo (ex: CONTROLE ATIVO, IDLE, CALIBRANDO).
* **Status do Motor:** Indica se as propriedades elétricas do motor já foram medidas (Calibrado / Sem Calibração).
* **Status do Encoder:** Indica se o alinhamento de fase do encoder foi concluído (Calibrado / Sem Calibração).
* **Status do Índice Z:** Mostra se o pulso de referência (Z) do encoder já foi encontrado.
* **Tensão da Fonte (DC):** A tensão elétrica atual lida no barramento principal de alimentação.
* **Corrente Iq:** A componente da corrente (em Amperes) que está sendo efetivamente utilizada para produzir torque.
* **Torque Atual:** Uma estimativa matemática (em Nm) da força que o motor está produzindo no exato momento, baseada na corrente Iq multiplicada pelo valor de Kt configurado.
* **Torque (Máx.):** Registra o maior pico de torque medido desde a última conexão ou desde o último clique no botão RST.

**⚠️ Importante:** Quando o **Status da ODrive** estiver em IDLE (inativo), as leituras de **Corrente Iq** e **Torque** podem apresentar ligeiras flutuações ou valores residuais aleatórios, e isso é completamente normal. Leituras de corrente precisas só são válidas quando o motor está ativado em malha fechada.

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
