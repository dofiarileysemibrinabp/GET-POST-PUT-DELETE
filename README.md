// Importa a biblioteca Express
const express = require('express');
const app = express();

// Middleware para processar JSON no corpo das requisições POST e PUT
app.use(express.json());

/**
 * Rota GET: Retorna uma mensagem de boas-vindas.
 * Teste no navegador ou com um cliente HTTP como Postman.
 */
app.get('/', (req, res) => {
    res.send('Requisição GET recebida! Bem-vindo ao servidor.');
});

/**
 * Rota POST: Recebe dados enviados no corpo da requisição.
 * Teste usando Postman ou curl:
 * curl -X POST -H "Content-Type: application/json" -d '{"nome":"João"}' http://localhost:8080/enviar
 */
app.post('/enviar', (req, res) => {
    const { nome } = req.body; // Captura o dado enviado no corpo
    res.send(`Requisição POST recebida! Nome enviado: ${nome || 'não informado'}`);
});

/**
 * Rota PUT: Atualiza informações e retorna uma mensagem de sucesso.
 * Teste com Postman ou curl:
 * curl -X PUT -H "Content-Type: application/json" -d '{"idade":30}' http://localhost:8080/atualizar
 */
app.put('/atualizar', (req, res) => {
    const { idade } = req.body; // Captura o dado enviado no corpo
    res.send(`Requisição PUT recebida! Idade atualizada para: ${idade || 'não informada'}`);
});

/**
 * Rota DELETE: Simula a exclusão de um recurso.
 * Teste com Postman ou curl:
 * curl -X DELETE http://localhost:8080/deletar
 */
app.delete('/deletar', (req, res) => {
    res.send('Requisição DELETE recebida! Recurso deletado com sucesso.');
});

// Define a porta do servidor
const PORT = 8080;

// Inicia o servidor e exibe a mensagem de sucesso no terminal
app.listen(PORT, () => {
    console.log(`Servidor rodando em http://localhost:${PORT}`);
});

/**
 * Passo a passo para rodar o servidor:
 * 
 * 1. Certifique-se de ter o Node.js instalado.
 * 2. Crie uma pasta e salve este arquivo como "server.js".
 * 3. Abra o terminal na pasta do arquivo e inicialize o npm:
 *    $ npm init -y
 * 
 * 4. Instale o Express:
 *    $ npm install express
 * 
 * 5. Inicie o servidor com o comando:
 *    $ node server.js
 * 
 * 6. Acesse as rotas:
 *    - GET: http://localhost:8080/
 *    - POST: http://localhost:8080/enviar
 *    - PUT: http://localhost:8080/atualizar
 *    - DELETE: http://localhost:8080/deletar
 * 
 * Teste as requisições GET no navegador e as demais com ferramentas como Postman ou curl.
 */
