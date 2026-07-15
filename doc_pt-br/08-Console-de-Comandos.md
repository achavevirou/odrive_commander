**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Console de Comandos**

A página "Console de Comandos" é uma ferramenta similar ao `odrivetool`. Ela oferece acesso direto para ler ou escrever qualquer parâmetro que seja válido para a ODrive nos eixos `axis0` ou `axis1`.

### **Como Usar**

O funcionamento é simples e direto:

1. **Digite o Comando:** No campo de texto, digite o comando Python exato que você usaria no `odrivetool`. O objeto que representa a sua ODrive na aplicação é o `dev0` (ou `odrv0`).  
2. **Execute:** Pressione a tecla **Enter** ou clique no botão **"Enviar Comando"**.  
3. **Veja o Resultado:** Se o comando enviado for válido, a resposta da ODrive ou o resultado do seu comando será impresso logo abaixo no histórico.

**Segurança no Histórico:** O console mantém um histórico de todos os comandos e respostas da sessão atual. Para garantir a integridade da interação, **o histórico não pode ser apagado ou editado manualmente**, prevenindo a execução acidental de comandos antigos.

### **Botões de Utilidade**

* **Copiar:** Copia todo o conteúdo do histórico do console para a área de transferência.  
* **Enviar Comando:** Executa o comando que você digitou.  
* **Limpar:** Apaga todo o histórico e reinicia o console com um novo prompt de entrada.

### **Exemplos de Comandos Padrão**

Você pode usar o console para ler ou alterar qualquer parâmetro da ODrive:

* **Para ler um valor:**  
  `dev0.vbus_voltage`  
  *(Exemplo de retorno: 24.101...)*  
* **Para alterar um valor:**  
  `dev0.axis0.controller.config.vel_limit = 25`  
  *(Este comando não retorna nada, mas altera o parâmetro na memória da ODrive)*

### **Comando Especial: Estimativa de Corrente**

A aplicação inclui um comando personalizado para ajudar a entender a relação entre torque e corrente para o seu motor:

* **Comando:** `dev0.axis0.current.estimate(valor_max_torque)`  
* **Função:** Utiliza a **Constante de Torque (Kt)** configurada para gerar uma tabela de estimativa. A tabela mostra a corrente Iq (em Amperes) necessária para produzir cada nível de torque (em Nm), desde 1 Nm até ao `valor_max_torque` que você especificar.  
* **Limite:** O `valor_max_torque` está limitado a 40 para garantir a legibilidade.  
* **Requisito:** O status da ODrive deve ser **CONTROLE ATIVO** (CLOSED LOOP CONTROL) para cálculos válidos.  
* **Exemplo:** `dev0.axis0.current.estimate(10)` gerará uma tabela para torques de 1 a 10 Nm.

### **Possíveis Erros no Console**

* **SyntaxError: invalid syntax:** Você digitou o comando incorretamente (ex: esqueceu o sinal de `=` ou cometeu um erro de digitação).  
* **AttributeError:** O parâmetro que você está tentando acessar não existe ou o caminho está errado (ex: `dev0.axis0.config.vel_lim` em vez do caminho correto).  
  * **Solução:** Consulte a documentação oficial da ODrive para validar o caminho do parâmetro.

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
