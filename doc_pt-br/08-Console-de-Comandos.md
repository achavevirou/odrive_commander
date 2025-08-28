
**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Console de Comandos**

A página "Console de Comandos" é uma ferramenta similar ao odrivetool. Ela oferece acesso direto para ler ou escrever qualquer parâmetro que seja válido para a ODrive nos eixos axis0 ou axis1.

### **Como Usar**

O funcionamento é simples e direto:

1. **Digite o Comando:** No campo de texto, digite o comando Python exato que você usaria no odrivetool. O objeto que representa a sua ODrive na aplicação é o odrv0 ou dev0.  
2. **Execute:** Pressione a tecla **Enter** ou clique no botão **"Enviar Comando"**.  
3. **Veja o Resultado:** Se o comando enviado for válido, a resposta da ODrive ou o resultado do seu comando será impresso logo abaixo no console.

O console mantém um histórico de todos os comandos e respostas da sessão atual. Para sua segurança, **o histórico não pode ser apagado ou editado**, prevenindo a execução acidental de comandos antigos.

### **Botões de Utilidade**

* **Copiar:** Copia todo o conteúdo do histórico do console para a área de transferência.  
* **Enviar Comando:** Executa o comando que você digitou.  
* **Limpar:** Apaga todo o histórico e reinicia o console.

### **Exemplos de Comandos Padrão**

Você pode usar o console para ler ou alterar qualquer parâmetro da ODrive.

* **Para ler um valor:**  
  dev0.vbus\_voltage

  *Exemplo de resultado: 24.101...*  
* **Para alterar um valor:**  
  dev0.axis0.controller.config.vel\_limit \= 25

  *(Este comando não retorna nada, mas o valor é alterado na ODrive)*

### **Comando Especial: Estimativa de Corrente**

A aplicação inclui um comando personalizado para ajudar a entender a relação entre torque e corrente para o seu motor.

* **Comando:** dev0.axis0.current.estimate(valor\_max\_torque)  
* **Função:** Este comando utiliza a **Constante de Torque (Kt)** configurada na sua ODrive para gerar uma tabela de estimativa. A tabela mostra a corrente Iq (em Amperes) que seria necessária para produzir cada nível de torque (em Nm), desde 1 Nm até ao valor\_max\_torque que você especificar.  
* **Limite:** O valor\_max\_torque está limitado a 40 para evitar tabelas excessivamente longas.  
* Para que esse comando possa gerar valores válidos de corrente, é necessário que o Status da ODrive seja CONTROLE ATIVO (CLOSED LOOP CONTROL).  
* **Exemplo de Uso:**  
  dev0.axis0.current.estimate(10)

  *Isto irá gerar uma tabela de estimativa de corrente para torques de 1 a 10 Nm.*

### **Possíveis Erros no Console**

Ao digitar comandos manualmente, é possível que a ODrive retorne um erro. O console irá exibir a mensagem de erro retornada e que geralmente é um erro padrão do Python. Os mais comuns são:

* **SyntaxError: invalid syntax**  
  * **Causa:** Você digitou o comando incorretamente (ex: dev0.vbusvoltage em vez de dev0.vbus\_voltage, ou esqueceu o sinal de \=).  
* **AttributeError: '... object' has no attribute '...'**  
  * **Causa:** O parâmetro que você está tentando acessar não existe. Isso pode acontecer se você digitou erroneamente o nome de um parâmetro (ex: dev0.axis0.config.vel\_lim em vez de dev0.axis0.controller.config.vel\_limit).  
  * **Solução:** Consulte a documentação oficial da ODrive para encontrar o nome e o caminho corretos do parâmetro que deseja alterar.

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).