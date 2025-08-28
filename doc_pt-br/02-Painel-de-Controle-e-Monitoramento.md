**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Painel de Controle e Monitoramento**

A interface principal do ODrive Commander está dividida em duas áreas sempre visíveis: o **Painel de Controle** à esquerda, onde todas as ações são iniciadas, e o **Painel de Monitoramento** à direita, que exibe dados da ODrive em tempo real.

## **Painel de Controle (Esquerda)**

Este painel contém todos os botões para interagir com a aplicação e com a ODrive.

### **1\. Conexão e Status**

* **Idioma:** Permite alternar a linguagem da interface entre Português (PT-BR) e Inglês (EN-US). A sua escolha é salva automaticamente e será lembrada na próxima vez que abrir a aplicação.  
* **Status:** Indica o estado atual da conexão.  
  * **Desconectado:** Não há ODrive conectada com a aplicação.  
  * **Conectando...:** A aplicação está procurando por uma ODrive conectada via USB.  
  * **Conectado:** A comunicação com a ODrive foi estabelecida com sucesso.  
* **Conectar/Desconectar ODrive:** O botão principal para iniciar ou terminar a comunicação com a placa.  
* **Reiniciar ODrive:** Envia um comando de reinicialização para a ODrive.  
* **Modo DFU:** Coloca a ODrive em modo DFU (SMT32 BOOTLOADER) para permitir carregamento de firmware.

### **2\. Navegação de Configurações**

Este grupo de botões funciona como um menu de navegação. Clicar em um botão abre a página de configuração correspondente na área principal da janela. O botão da página atualmente selecionada fica destacado.

* **Resistor, CAN, Motor, Encoder:** Abre as respectivas páginas de configuração.  
* **Verificar Erros na ODrive:** Abre uma tela que exibe os erros atuais da ODrive.  
* **Console de Comandos:** Abre o console interativo.

### **3\. Utilitários**

Este grupo oferece acesso rápido a funções importantes de gestão e controle.

* **Ativar/Desativar Eixo:** Alterna o estado do motor entre "ativo" (em malha fechada) e "inativo/IDLE" (motor livre).  
* **Exportar Configuração:** Abre uma janela para salvar todos os parâmetros atuais da ODrive em um arquivo de texto (.json). É ideal para fazer backups.  
* **Carregar Configuração:** Abre uma janela para carregar os parâmetros de um arquivo .json para a memória da ODrive. **Atenção:** As configurações carregadas só se tornam permanentes após clicar em "Salvar Configurações".  
* **Excluir Configuração:** Apaga permanentemente a configuração salva na memória da ODrive, revertendo-a para os padrões de fábrica, e reinicia a placa. **Use com cuidado\!**

## **Painel de Monitoramento**

Assim que a conexão é estabelecida, este painel é preenchido com dados lidos diretamente da ODrive e atualizados a cada segundo.

\<\!-- Sugestão: Recorte a imagem para focar nesta seção \--\>

* **Status da ODrive:** Mostra o estado atual do eixo (ex: CONTROLE ATIVO, IDLE, CALIBRANDO).  
* **Status do Motor / Encoder:** Indica se o motor e o encoder já foram calibrados.  
* **Status do Índice Z:** Mostra se o pulso de índice do encoder foi encontrado.  
* **Corrente Positiva (Máx):** O limite de corrente que o motor pode consumir.  
* **Corrente Negativa (Máx):** O limite de corrente de regeneração.  
* **Range de Corrente (Máx):** O pico de corrente que os MOSFETs podem suportar.  
* **Constante de Torque:** O valor de Kt (constante de torque) configurado.  
* **Tensão DC:** A tensão atual do barramento de alimentação.  
* **Corrente Fase A/B/C:** A corrente medida em cada uma das três fases do motor.  
* **Corrente Iq:** A componente da corrente que efetivamente produz torque.  
* **Torque:** Uma estimativa do torque que o motor está produzindo, calculada em tempo real.

**⚠️ Importante:** Quando o **Status da ODrive** estiver em IDLE (inativo), as leituras de **Corrente Fase A, B, C** e **Corrente Iq** podem apresentar valores aleatórios, e isso é normal. Leituras de corrente precisas só são válidas quando o motor está em **CONTROLE ATIVO** (malha fechada).

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).