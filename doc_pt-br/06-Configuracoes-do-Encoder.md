
**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações do Encoder**

O Encoder é fundamental para que a ODrive saiba a posição exata do motor a cada instante. Uma configuração correta do encoder é essencial para um Force Feedback estável, preciso e sem vibrações.

Esta aplicação foca na configuração de **encoders incrementais**, que são o tipo mais comum em projetos de volantes Direct Drive DIY.

### **Parâmetros e Funções da Página**

* **Tipo de Encoder:**  
  * **Função:** Define o tipo de encoder utilizado.  
  * **Como preencher:** Atualmente, a aplicação está focada no modo **Incremental**, que deve ser mantido para a maioria dos encoders de quadratura (A, B, Z).  
* **CPR do Encoder (PPR x 4):**  
  * **Função:** CPR significa "Counts Per Revolution" (Contagens por Rotação). É o número total de "passos" que o encoder consegue detectar em uma volta completa.  
  * **Como preencher:** Este valor é **quatro vezes** o valor de PPR ("Pulses Per Revolution") do seu encoder. Se o seu encoder tem 1024 PPR, o valor de CPR a ser inserido é 4096\. Consulte a folha de dados do seu encoder para encontrar o valor de PPR.  
* **Habilitar Uso do Índice Z:**  
  * **Função:** Ativa o uso do sinal de Índice (também chamado de "Z" ou "referência").  
  * **Como preencher:** Marque esta caixa **apenas se o seu encoder tiver um sinal de Índice Z** e se ele estiver corretamente conectado na ODrive.  
* **Calibração Completa do Eixo:**  
  * Inicia a rotina completa de calibração (FULL\_CALIBRATION\_SEQUENCE). Durante este processo, a ODrive irá girar o motor para medir seus parâmetros elétricos e, em seguida, alinhar o encoder com as fases do motor. Após o sucesso, os dados da calibração ficam guardados na memória temporária da ODrive.  
* **Configurações de Inicialização (Startup):**  
  * **Buscar Índice Z ao Iniciar:** Se marcada, a ODrive irá procurar pelo pulso de índice automaticamente sempre que for ligada. **Atenção:** Esta opção só pode ser ativada se a opção "Habilitar Uso do Índice Z" também estiver marcada.  
  * **Encoder Pré Calibrado:** Se marcada, a ODrive pula a rotina de alinhamento do encoder na inicialização. **Atenção:** Esta opção só pode ser ativada se a opção "Habilitar Uso do Índice Z" também estiver marcada.  
  * **Motor Pré Calibrado:** Se marcada, a ODrive pula a medição de resistência e indutância do motor na inicialização.  
  * **Calibrar Offset ao Iniciar:** Se marcada, a ODrive realizará a rotina de alinhamento do encoder toda vez que for ligada.  
  * **Controle de Malha Fechada ao Iniciar:** Se marcada, a ODrive ativa o motor (entra em modo de controle ativo) assim que a inicialização e as verificações terminarem.  
* **Buscar Índice Z:**  
  * Este botão envia um comando ao motor para que seja encontrado o pulso de referência Z do encoder. **Atenção:** Esse comando só pode ser usado se a opção "Habilitar Uso do Índice Z" também estiver marcada.

### **Passo a Passo: Processo de Calibração**

Existem dois fluxos de trabalho para a calibração, dependendo se o seu encoder utiliza ou não o sinal de Índice Z.

**⚠️ Importante sobre Carregar Arquivos .json:** Se você usou a função "Carregar Configuração" para importar um arquivo .json, por segurança, você **DEVE** realizar uma nova calibração completa seguindo um dos cenários abaixo após importar **QUALQUER** arquivo de configuração, mesmo que seja o seu próprio.

**⚠️ Importante:** Para qualquer um dos processos de calibração abaixo, o eixo do motor deve estar **completamente livre para girar**, sem nenhuma carga, peso ou obstrução. Qualquer resistência pode levar a uma calibração incorreta e causar erros.

#### **Cenário 1: Calibração do Encoder COM Índice Z**

1. **Configuração Inicial:** Configure os parâmetros Tipo de Encoder, CPR do Encoder e marque a caixa Habilitar Uso do Índice Z. Após configurar, clique em **"Aplicar Configurações do Encoder"**.  
2. **Calibração Completa:** Clique no botão **"Calibração Completa do Eixo"**. Aguarde o motor emitir um "beep", procurar pelo Índice Z e finalizar a calibração.  
3. **Habilitar Opções de Inicialização:** Após a calibração ser concluída com sucesso, marque as seguintes caixas:  
   * \[X\] Buscar Índice Z ao Iniciar  
   * \[X\] Encoder Pré Calibrado  
   * \[X\] Motor Pré Calibrado  
   * \[X\] Controle de Malha Fechada ao Iniciar  
4. **Aplicar e Salvar:** Clique primeiro em **"Aplicar Configurações do Encoder"** e, em seguida, no botão principal **"Salvar Configurações"** para tornar as alterações permanentes.

#### **Cenário 2: Calibração do Encoder SEM Índice Z**

1. **Configuração Inicial:** Configure os parâmetros Tipo de Encoder e CPR do Encoder. Certifique-se de que a caixa Habilitar Uso do Índice Z esteja **desmarcada**. Após configurar, clique em **"Aplicar Configurações do Encoder"**.  
2. **Calibração Completa:** Clique no botão **"Calibração Completa do Eixo"**. Aguarde o motor emitir um "beep", e então girar e parar.  
3. **Habilitar Opções de Inicialização:** Após a calibração ser concluída com sucesso, marque as seguintes caixas:  
   * \[X\] Motor Pré Calibrado  
   * \[X\] Calibrar Offset ao Iniciar  
   * \[X\] Controle de Malha Fechada ao Iniciar  
4. **Aplicar e Salvar:** Clique primeiro em **"Aplicar Configurações do Encoder"** e, em seguida, no botão principal **"Salvar Configurações"** para tornar as alterações permanentes.

### **Solução de Problemas: Índice Z não é encontrado?**

A busca pelo Índice Z pode falhar se houver ruído elétrico no sinal. Se você tem certeza de que a sua fiação está correta mas a busca falha repetidamente ou então a aplicação informa que encontrou o Z, mas durante a calibração/inicialização o Z não é encontrado, experimente as seguintes soluções:

* **Filtro Capacitivo:** A primeira linha de defesa contra ruído de alta frequência é soldar um **capacitor cerâmico de 22nF a 47nF** entre o pino do sinal do Índice Z e o pino GND. Este filtro deve ser montado o mais próximo possível da placa do encoder para máxima eficácia.  
* **Use Cabo Blindado:** Como uma medida adicional, utilize sempre um cabo blindado para a conexão do encoder, garantindo que a malha de blindagem esteja conectada ao pino GND.

*Após aplicar qualquer uma destas soluções de hardware, execute a **Calibração Completa do Eixo** novamente.*

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).