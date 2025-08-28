
**Nota de Compatibilidade:** Esta documentação e a aplicação ODrive Commander v1.0 são destinadas ao uso com placas **ODrive | XDrive | Odesc** que estejam executando o **firmware v0.5.6**. Funcionalidades e parâmetros podem ser diferentes em outras versões de firmware.

# **Diagnóstico de Erros**

A página "Verificar Erros na ODrive" é a sua principal ferramenta para diagnosticar problemas com o motor, o encoder ou a própria controladora. Quando algo não funciona como esperado (por exemplo, o motor não gira ou emite bipes), esta é a primeira página que você deve consultar.

### **Como Usar**

1. **Navegue até à Página:** No painel de controle esquerdo, clique no botão **"Verificar Erros na ODrive"**.  
2. **Análise Automática:** A aplicação executa automaticamente o comando para ler os erros e exibe o resultado na caixa de texto.  
3. **Interpretação:** O texto mostra o status de cada componente principal do axis0. Se tudo estiver correto, cada item mostrará no error. Se houver um problema, o código do erro será exibido (ex: AxisError.MOTOR\_FAILED).  
4. **Copiar para Ajuda:** Se você não souber como resolver um erro, pode usar o botão **"Copiar"** para copiar todo o log de erros para a sua área de transferência. Isso é extremamente útil para colar o log no Google ou Discord, por exemplo, para buscar respostas que resolvam o problema.

### **Limpando os Erros**

Muitos erros na ODrive são "travados" (latched), o que significa que eles permanecem ativos mesmo que a causa do problema já tenha sido resolvida. Para limpar os erros, esta página tem um botão **"Limpar Erros"**.

Ao clicar neste botão, a aplicação envia o comando de limpeza para a ODrive (especificamente, dump\_errors(odrv0, True)), que apaga todos os erros ativos.

Após limpar os erros, tente ativar o eixo novamente. Se o erro reaparecer, significa que a causa raiz do problema ainda precisa ser corrigida.

Voltar a [Página Inicial da Documentação do ODrive Commander](https://github.com/achavevirou/odrive_commander/blob/main/doc_pt-br/01-Pagina-Inicial-da-Documentacao.md).