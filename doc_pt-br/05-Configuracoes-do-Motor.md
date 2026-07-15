**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações do Motor**

A parte de configurações do Motor é uma das mais importantes para o bom funcionamento de um volante Direct Drive. É aqui que você informa à ODrive as características físicas e elétricas do seu motor. Parâmetros incorretos nesta aba podem resultar em superaquecimento, vibrações indesejadas, desarmes de proteção ou um Force Feedback impreciso.

### **Parâmetros de Configuração**

* **Pares de Polos:**  
  * **Função:** O número de pares de ímãs dentro do seu motor. Este valor é fundamental para que a ODrive saiba como comutar as fases corretamente para fazer o motor girar.  
  * **Como preencher:** Conte o número total de ímãs do seu motor e divida por 2. (Ex: um motor com 30 ímãs tem 15 pares de polos). Motores industriais costumam ter essa informação explícita no datasheet.  

* **Tensão de Calibração (V) / Corrente de Calibração (A):**  
  * **Função:** Estes valores são utilizados durante a rotina de calibração para medir a resistência e a indutância dos enrolamentos do motor (o famoso "bip" inicial).  
  * **Como preencher:** Para a maioria dos motores de Direct Drive, os valores padrão (10.0V e 10.0A) são um bom ponto de partida. Se o seu motor for muito pequeno ou apresentar superaquecimento no teste, reduza a corrente de calibração.  

* **Constante de Torque (Kt):**  
  * **Função:** Este é o parâmetro **mais crítico** para um Force Feedback preciso. Ele define a relação entre a corrente elétrica (em Amperes) e o torque mecânico (em Newton-metro). Um valor de Kt correto garante que, quando o simulador pede 2 Nm de força, a ODrive envie a quantidade exata de corrente para gerar esses 2 Nm.  
  * **Como preencher:** Você pode obter este valor dividindo o **torque nominal** do motor pela sua **corrente nominal** (Torque Nominal / Corrente Nominal = Kt). Motores servo industriais de alto torque (como a série 130ST) possuem valores de Kt elevados, gerando muito mais força com menor consumo de corrente quando comparados a motores comuns de hoverboard. Nunca defina este valor como zero.  

* **Limite de Corrente (A) e Margem de Corrente (A):**  
  * **Função:** O **Limite** é a restrição contínua máxima de corrente de fase que a ODrive enviará para o motor. A **Margem** permite picos transitórios de corrente acima do limite estrito antes que a placa desarme por erro de sobrecorrente.  
  * **Como preencher:** Para descobrir o limite ideal do seu hardware, divida o **torque de pico** do motor pelo valor de **Kt** calculado acima; o resultado será a corrente máxima que pode ser consumida. A Margem de Corrente pode ser preenchida com um valor de "folga" (ex: 5.0A a 10.0A) acima desse limite para suportar picos súbitos e rápidos do Force Feedback sem interromper a simulação.  

* **Range de Corrente (A):**  
  * **Função:** Configura os amplificadores operacionais da ODrive para otimizar a leitura da corrente de fase numa determinada faixa.  
  * **Como preencher:** Sugere-se que este valor seja determinado a partir da soma exata do valor do **Limite de Corrente** + valor da **Margem de Corrente** + uma folga de **3 a 4A**.  

* **Controle de Corrente (rad/s):**  
  * **Função:** A largura de banda (velocidade de resposta) do controlador de corrente da ODrive. Valores muito altos deixam o motor "rígido", mas podem gerar ruído de alta frequência (assobio).  
  * **Como preencher:** O padrão costuma ficar entre 100.0 e 1000.0, dependendo da indutância do seu motor.  

* **Tipo de Motor / Modo de Controle:**  
  * **Função:** Para o uso como volante Direct Drive com OpenFFBoard, a ODrive deve focar inteiramente em fornecer torque limpo.  
  * **Como preencher:** O software já trava essas opções em "Alta Corrente" e "Torque" para evitar configurações acidentais.  

* **Limites de Potência para Spinout (W):**  
  * **Função:** Define quanta potência elétrica e mecânica o motor pode dissipar antes que a controladora considere que ele "perdeu o controle" e corte o eixo.  
  * **Como preencher:** Em simuladores, movimentos rápidos do volante podem gerar picos estranhos. Ajustar a Potência Elétrica (ex: 100.0) e a Potência Mecânica (que exige um valor negativo, ex: -50.0) previne desarmes desnecessários durante drift ou colisões severas virtuais.  

### **Configurações Avançadas e Proteções**

* **Sem Erro de excesso de velocidade / Sem Limite de Velocidade:**  
  Marcando essas caixas, a ODrive não cortará a força caso o volante gire muito rápido repentinamente. Essencial para Force Feedback livre.  

* **Compensação de Back-EMF / Compensação R/L:**  
  * **Função:** Melhoram ativamente a resposta e o rastreamento da corrente em rotações mais altas, anulando os efeitos resistivos e a tensão contrária que o motor gera naturalmente ao girar.  

Depois de ajustar os parâmetros, clique no botão **"Aplicar Configurações do Motor"** para enviar os valores. Lembre-se de que as alterações só se tornam permanentes após clicar no botão principal **"Salvar Configurações"**.

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
