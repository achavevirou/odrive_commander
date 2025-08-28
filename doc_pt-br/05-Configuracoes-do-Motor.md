
**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações do Motor**

A parte de configurações do Motor é uma das mais importantes para o bom funcionamento de um volante Direct Drive. É aqui que você informa à ODrive as características físicas e elétricas do seu motor. Parâmetros incorretos nesta seção podem resultar em superaquecimento, vibrações indesejadas ou um Force Feedback fraco e impreciso.

### **Parâmetros de Configuração**

* **Pares de Polos:**  
  * **Função:** O número de pares de ímãs dentro do seu motor. Este valor é fundamental para que a ODrive saiba como comutar as fases corretamente para fazer o motor girar.  
  * **Como preencher:** Conte o número total de ímãs do seu motor e divida por 2\. Por exemplo, um motor com 30 ímãs tem 15 pares de polos.  
* **Tensão de Calibração (V) / Corrente de Calibração (A):**  
  * **Função:** Estes valores são utilizados durante a rotina de calibração para medir a resistência e a indutância do motor.  
  * **Como preencher:** Para a maioria dos motores de Direct Drive, os valores padrão (10.0V e 10.0A) são um bom ponto de partida. Se o seu motor for muito pequeno, pode ser necessário reduzir a corrente de calibração para evitar superaquecimento durante o processo.  
* **Constante de Torque (Kt):**  
  * **Função:** Este é o parâmetro **mais crítico** para um Force Feedback preciso. Ele define a relação entre a corrente elétrica (em Amperes) e o torque mecânico (em Nm/Newton metro). Um valor de Kt correto garante que, quando o simulador pede 2 Nm de força, a ODrive envie a quantidade exata de corrente para o motor gerar esses 2Nm.  
  * **Como preencher:** O valor de Kt geralmente é fornecido pelo fabricante no datasheet do motor. Para motor de hoverboard, um Kt \= 0.49 é um bom valor.  
* **Limite de Corrente (A):**  
  * **Função:** Uma proteção vital. Este é o limite máximo de **corrente de fase** que a ODrive irá enviar para os enrolamentos do motor.  
  * **Importante:** Esta **NÃO** é a corrente que a sua fonte de alimentação precisa fornecer. A corrente nas fases do motor pode ser muito mais alta que a corrente puxada da fonte (corrente do barramento DC), especialmente em baixas velocidades e alto torque \- um cenário típico de Force Feedback.  
  * **Como preencher:** Consulte a folha de dados do seu motor para encontrar a "corrente nominal" ou "corrente contínua" e use um valor próximo para proteger o motor.

#### **Como a Corrente de Fase pode ser maior que a da Fonte?**

A ODrive recebe uma corrente contínua (DC) da sua fonte, mas um motor brushless precisa de correntes que se assemelham a ondas senoidais (AC) para girar. Para conseguir isso, a controladora usa uma técnica chamada **PWM (Pulse Width Modulation)**.

De forma simplificada, a ODrive liga e desliga os seus interruptores eletrônicos (MOSFETs) milhares de vezes por segundo. Ao controlar a duração desses pulsos, ela consegue "moldar" a corrente DC da fonte, transformando-a na corrente de fase necessária para criar o campo magnético que gera o torque.

Como essa corrente circula pelos enrolamentos do motor em alta frequência, ela pode atingir picos muito mais altos do que a corrente média que está sendo puxada da fonte de alimentação. É por isso que o seu motor pode estar trabalhando com 40A de corrente de fase, enquanto a sua fonte está fornecendo apenas 5A ou 10A de corrente DC.

* **Range de Corrente (A):**  
  * **Função:** Configura o hardware da ODrive para otimizar a medição da **corrente de fase** numa determinada faixa.  
  * **Como preencher:** Este valor deve ser ligeiramente superior ao "Limite de Corrente". Se o seu limite de corrente é 40A, um range de 50A é uma escolha segura. Este valor também não se refere à corrente da sua fonte de alimentação.  
* **Controle de Corrente (Hz):**  
  * **Função:** A largura de banda do controlador de corrente. Valores mais altos podem resultar numa resposta mais "rígida" e rápida, mas também podem introduzir ruído audível (assobio) no motor.  
  * **Como preencher:** O valor padrão de 100.0 é geralmente adequado.  
* **Tipo de Motor / Modo de Controle:**  
  * **Função:** Para a aplicação com OpenFFBoard, estes modos devem ser fixos.  
  * **Como preencher:** A aplicação foi projetada para configurar a ODrive para Tipo de Motor apenas como Alta Corrente e o Modo de Controle apenas como Torque.  
* **Proteções (Spinout e Limites):**  
  * **Função:** Estas são proteções de software para evitar que o motor perca o controle (spinout) ou exceda limites de velocidade.  
  * **Como preencher:** Para aplicações de Force Feedback, onde a resposta precisa ser o mais livre possível, é comum **desativar estas proteções**, marcando as checkboxes correspondentes. Para spinout é necessário testar valores, mas 100 e -30 são bons valores para começar.

Depois de ajustar os parâmetros, clique no botão "**Aplicar Configurações do Motor**" para enviar os valores para a ODrive. Lembre-se de que as alterações só se tornam permanentes após clicar em "**Salvar Configurações**".

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).