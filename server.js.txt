import express from "express";
import bodyParser from "body-parser";
import cors from "cors";
import { io } from "socket.io-client";

const app = express();
app.use(bodyParser.json());


const WS_URL = "wss://api-in.pocketoption.com:8095/socket.io/?EIO=3&transport=websocket";

// Rota teste
app.get("/", (req, res) => {
  res.send("?? Backend PocketOption rodando no Render!");
});

// Exemplo de endpoint saldo
app.post("/saldo", (req, res) => {
  const { ssid } = req.body;
  // Aqui depois você coloca a lógica de conexão com a API PocketOption
  res.json({ saldo: 1000, ssidRecebido: ssid });
});

// Porta dinâmica do Render
app.listen(process.env.PORT || 8000, () => {
  console.log(`Servidor rodando na porta ${process.env.PORT || 8000}`);
});
