**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.2 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Diagnóstico de Erros**

A página "Verificar Erros na ODrive" é a sua principal ferramenta para diagnosticar problemas com o motor, o encoder ou a própria controladora. Quando algo não funciona como esperado (por exemplo, o motor não gira, bloqueia ou emite bipes de aviso), esta é a primeira aba que você deve consultar.

### **Como Usar**

1. **Navegue até à Página:** No painel de controle esquerdo, clique no botão **"Verificar Erros na ODrive"**.  
2. **Análise Automática:** A aplicação executa automaticamente o comando para ler os erros da placa e exibe o resultado detalhado na caixa de texto.  
3. **Interpretação:** O texto exibido detalha o status de cada componente principal do eixo selecionado (ex: `AxisError.MOTOR_FAILED` ou `EncoderError.ABS_SPI_TIMEOUT`). Se tudo estiver correto, cada item mostrará `no error`.  
4. **Copiar para Ajuda:** Se você não souber como resolver um erro, utilize o botão **"Copiar"**. Isso transfere todo o log de erros para a sua área de transferência, facilitando a partilha em comunidades, Discord ou fóruns de suporte para buscar orientações precisas.

### **Limpando os Erros**

Muitos erros na ODrive são "travados" (latched), o que significa que eles permanecem ativos na memória da placa mesmo que a causa física do problema já tenha sido removida (como uma falha de comunicação momentânea ou um pico de tensão).

* **Botão "Limpar Erros":** Ao clicar neste botão, a aplicação envia o comando de limpeza para a ODrive (`dump_errors(odrv0, True)`). Isso apaga todos os códigos de erro ativos.

**⚠️ Recomendação:** Após limpar os erros, tente ativar o eixo novamente. Se o erro reaparecer instantaneamente após a ativação, significa que a causa raiz do problema ainda persiste e deve ser investigada nas abas de configuração (Motor, Encoder ou Proteções).

---
Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).
