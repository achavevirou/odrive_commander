**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações de CAN**

A interface de comunicação CAN (Controller Area Network) é um protocolo robusto usado em ambientes industriais e automotivos. No contexto de um volante Direct Drive com Force Feedback, a comunicação CAN é o método utilizado para que a **ODrive** se comunique com a placa controladora principal (STM32) que roda o firmware do **OpenFFBoard**.

Nesta aba é possível configurar os parâmetros essenciais para estabelecer essa comunicação.

### **Contexto: ODrive e OpenFFBoard**

Para que o seu volante funcione, a placa com OpenFFBoard precisa enviar comandos de torque para a ODrive e receber informações de volta. A comunicação via CAN é ideal para isso por ser rápida e resistente a ruídos elétricos.

Todos os dispositivos na mesma rede CAN devem partilhar a mesma velocidade (Baud Rate) e cada um deve ter um endereço (ID do Nó) único.

### **Parâmetros de Configuração**

* **ID do Nó:**  
  * **Função:** Define o endereço único do eixo atualmente selecionado (axis0 ou axis1) na rede CAN. O OpenFFBoard irá enviar os comandos de Force Feedback para este endereço.  
  * **Como preencher:** O valor padrão na ODrive é geralmente `0` para o axis0 e `1` para o axis1. Se você tiver apenas uma ODrive e uma placa OpenFFBoard com as configurações padrão, pode manter o eixo principal como `0`.  
* **Velocidade (Baud Rate):**  
  * **Função:** Define a velocidade de comunicação da rede CAN, medida em bits por segundo (bps). **Atenção:** Esta configuração afeta a placa inteira, independentemente do eixo selecionado.  
  * **Como preencher:** Para garantir a compatibilidade com o OpenFFBoard, este valor deve ser **exatamente o mesmo** que está configurado no firmware do OpenFFBoard. A configuração padrão e recomendada para o OpenFFBoard é **1000000** (1 Mbps).

Depois de ajustar os parâmetros, clique no botão **"Aplicar Configurações da CAN"** para enviar os valores para a memória RAM da ODrive. Lembre-se de que as alterações só se tornam permanentes após clicar no botão principal **"Salvar Configurações"**.

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
