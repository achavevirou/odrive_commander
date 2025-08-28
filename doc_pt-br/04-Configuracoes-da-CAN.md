
**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Configurações de CAN**

A interface de comunicação CAN (Controller Area Network) é um protocolo robusto usado em ambientes industriais e automotivos. No contexto de um volante Direct Drive com Force Feedback, a comunicação CAN é o método utilizado para que a **ODrive** se comunique com a placa controladora principal (STM32) que roda o firmware do **OpenFFBoard**.

Nesta parte é possível configurar os parâmetros essenciais para estabelecer essa comunicação.

### **Contexto: ODrive e OpenFFBoard**

Para que o seu volante funcione, a placa com OpenFFBoard precisa enviar comandos de torque para a ODrive e receber informações de volta. A comunicação via CAN é ideal para isso por ser rápida e resistente a ruídos elétricos.

Todos os dispositivos na mesma rede CAN devem partilhar a mesma velocidade (Baud Rate) e cada um deve ter um endereço (ID do Nó) único.

### **Parâmetros de Configuração**

* **ID do Nó:**  
  * **Função:** Define o endereço único da ODrive (especificamente do axis0) na rede CAN. O OpenFFBoard irá enviar comandos para este endereço.  
  * **Como preencher:** O valor padrão para o axis0 da ODrive é geralmente 0\. Se você tiver apenas uma ODrive e uma placa OpenFFBoard, pode manter este valor.  
* **Velocidade (Baud Rate):**  
  * **Função:** Define a velocidade de comunicação da rede CAN, medida em bits por segundo (bps).  
  * **Como preencher:** Para garantir a compatibilidade com o OpenFFBoard, este valor deve ser **exatamente o mesmo** que está configurado no firmware do OpenFFBoard. A configuração padrão e recomendada para o OpenFFBoard é **1000000** (1 Mbps).

Depois de ajustar os parâmetros, clique no botão **"Aplicar Configurações da CAN"** para enviar os valores para a ODrive. Lembre-se de que as alterações só se tornam permanentes após clicar em **"Salvar Configurações"**.

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).