**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Proteções**

A aba de Proteções permite configurar os parâmetros relacionados ao resistor de frenagem e aos limites de corrente contínua (DC) da fonte de alimentação. Estes componentes e configurações são cruciais para proteger a ODrive, o seu motor e a sua fonte contra picos de tensão e sobrecargas.

### **O que é o Resistor de Frenagem?**

Quando um motor elétrico é desacelerado bruscamente ou sofre uma força contrária rápida (como bater virtualmente em um muro no simulador), ele passa a atuar como um gerador, convertendo energia mecânica em energia elétrica. Essa energia é enviada de volta para a ODrive, o que faz a tensão no barramento DC subir rapidamente.

Se essa tensão subir além do limite, a ODrive desarmará a controladora com um erro (`DC_BUS_OVER_VOLTAGE`) para proteger os seus capacitores. O resistor de frenagem é um componente físico externo que atua como um "ralo" para essa energia reversa, dissipando-a instantaneamente na forma de calor e mantendo o sistema estável.

### **Parâmetros de Configuração**

* **Habilitar Resistor de Frenagem:**  
  * **Função:** Ativa ou desativa o uso do resistor de frenagem pela controladora.  
  * **Quando marcar:** Marque esta caixa **obrigatoriamente** se você tiver um resistor de frenagem fisicamente conectado aos bornes auxiliares (AUX) da sua ODrive.  
* **Resistência (Ω):**  
  * **Função:** O valor da resistência elétrica do seu componente de frenagem, medido em Ohms (Ω).  
  * **Como preencher:** Insira o valor nominal do seu resistor (ex: `10.0` ou `12.0`). Se a placa estiver desarmando com picos de tensão mesmo com o resistor ligado, você pode experimentar inserir no software um valor ligeiramente inferior ao valor físico real para forçar a ODrive a dissipar a energia de forma mais antecipada.  
* **Corrente DC Negativa Máxima (A):**  
  * **Função:** Define o limite máximo de corrente que a ODrive tem permissão para "devolver" em direção à fonte de alimentação.  
  * **Como preencher:** O valor deve conter obrigatoriamente o sinal negativo (`-`). Ajuste este parâmetro para permitir uma margem segura de corrente reversa, ajudando a evitar que a controladora desarme ou acione proteções indesejadas durante os picos bruscos de Force Feedback.  
* **Corrente DC Positiva Máxima (A):**  
  * **Função:** Define o teto máximo absoluto de corrente contínua que a ODrive tem permissão para puxar da sua fonte de alimentação.  
  * **Como preencher:** Insira a capacidade nominal de corrente da sua fonte em Amperes. Por exemplo, se a sua fonte fornece 48V e 10A, preencha com `10.0`. Isso impede que a controladora desarme ou queime a fonte em cenários onde o motor exige picos extremos de potência.

Depois de ajustar os parâmetros, clique no botão **"Aplicar Configurações de Proteção"** para enviar os valores para a memória RAM da ODrive. Lembre-se de que as alterações só se tornam permanentes após clicar no botão principal **"Salvar Configurações"**.

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
