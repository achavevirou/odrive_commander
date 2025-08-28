**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações do Resistor**

Permite configurar os parâmetros relacionados ao resistor de frenagem (ou resistor de dreno). Este componente é crucial para proteger a ODrive e a sua fonte de alimentação contra picos de tensão gerados pelo motor.

### **O que é o Resistor de Frenagem?**

Quando um motor elétrico é desacelerado bruscamente ou quando uma carga "empurra" o motor, ele atua como um gerador, convertendo energia mecânica em energia elétrica. Essa energia é enviada de volta para a ODrive, aumentando a tensão no barramento DC.

Se essa tensão subir demais, pode danificar a ODrive ou a fonte de alimentação. O resistor de frenagem é um componente físico que serve como um "ralo" para essa energia extra, dissipando-a na forma de calor.

### **Parâmetros de Configuração**

* **Habilitar Resistor:**  
  * **Função:** Ativa ou desativa o uso do resistor de frenagem.  
  * **Quando marcar:** Marque esta caixa **obrigatoriamente** se você tem um resistor de frenagem fisicamente conectado à sua ODrive.  
* **Resistência (Ω):**  
  * **Função:** O valor da resistência elétrica do seu resistor, medido em Ohms (Ω).  
  * **Como preencher:** Insira o valor nominal do seu resistor. Por exemplo, se o seu resistor é de 10 Ohms, digite 10.0. É crucial que este valor seja preciso.  
* **Corrente Negativa Máxima (A):**  
  * **Função:** Define o limite máximo de corrente que pode ser regenerada e enviada de volta para a fonte de alimentação.  
  * **Como preencher:** O valor deve ser negativo. Um valor comum para fontes de alimentação que não suportam regeneração é um número pequeno, como \-2.0 ou \-3.0 amperes.

Depois de ajustar os parâmetros, clique no botão **"Aplicar Configurações do Resistor"** para enviar os valores para a ODrive. Lembre-se de que as alterações só se tornam permanentes após clicar em **"Salvar Configurações"**.

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).