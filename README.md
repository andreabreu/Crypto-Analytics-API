# Crypto Analytics API

## Visão Geral

Crypto Analytics API é uma aplicação desenvolvida em Python para coletar e processar dados de criptomoedas. Ela utiliza a API da Binance para buscar informações de mercado em tempo real e permite que desenvolvedores integrem facilmente dados financeiros de criptomoedas em seus próprios sistemas, usando uma API RESTful.

## Funcionalidades

- **Consulta de Preços em Tempo Real**: Consulte os preços atuais de criptomoedas.
- **Indicadores Técnicos**: Acesse dados como Média Móvel Simples (SMA), Média Móvel Exponencial (EMA) e Índice de Força Relativa (RSI).
- **Tendências de Volume e Variação**: Acompanhe o volume e a variação dos preços para uma visão completa do mercado.
- **Dados Históricos**: Consulte o histórico de preços e volume para análise de tendências.

## Tecnologias Utilizadas

- **Python**
- **Flask** (ou FastAPI) para criação da API
- **SQLite/PostgreSQL** para banco de dados
- **Binance API** para coleta de dados de mercado
- **Docker** para containerização e fácil deploy

## Estrutura do Projeto

```plaintext:
crypto-analytics-api/
├── README.md
├── requirements.txt
├── app/
│   ├── main.py              # Ponto de entrada da API
│   ├── config.py            # Configuração da API e credenciais da exchange
│   ├── db.py                # Configuração e operações de banco de dados
│   ├── routes.py            # Endpoints da API
│   ├── services/
│   │   ├── data_collector.py # Coletor de dados da exchange
│   │   ├── analytics.py     # Cálculo de indicadores financeiros
│   │   └── utils.py         # Utilidades gerais
└── Dockerfile               # Configuração do Docker para deploy
```
## Configuração

### Pré-requisitos

1. Python 3.8+
2. Conta na Binance e chave da API.
3. Docker (opcional, para deploy)

### Instalação

Clone o repositório e instale as dependências:

bash:
git clone https://github.com/andreabreu/crypto-analytics-api.git
cd crypto-analytics-api
pip install -r requirements.txt

### Configuração da API da Binance

Crie um arquivo `.env` na raiz do projeto e adicione as seguintes variáveis:

```plaintext:
BINANCE_API_KEY="sua-chave-da-api"
BINANCE_SECRET_KEY="sua-chave-secreta"
```
Configure o banco de dados no arquivo `config.py`.

### Executando a Aplicação

Para rodar localmente, execute o seguinte comando:

```bash:
python app/main.py
```
A aplicação estará disponível em `http://localhost:5000`.

## Endpoints da API

- **GET /api/prices**: Retorna o preço atual das principais criptomoedas.
- **GET /api/volume**: Retorna o volume de negociação para as principais criptomoedas.
- **GET /api/indicators**: Retorna indicadores financeiros (SMA, EMA, RSI) de uma criptomoeda especificada.
- **GET /api/history**: Retorna dados históricos de uma criptomoeda.

## Exemplo de Uso com C#

Para integrar esta API em uma aplicação C#, utilize o seguinte exemplo:

```csharp:
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace CryptoAnalyticsClient
{
    class Program
    {
        static async Task Main(string[] args)
        {
            HttpClient client = new HttpClient();
            client.BaseAddress = new Uri("http://localhost:5000");

            HttpResponseMessage response = await client.GetAsync("/api/prices");
            string data = await response.Content.ReadAsStringAsync();
            Console.WriteLine("Preços de criptomoedas: " + data);
        }
    }
}
```
## Contribuindo

Sinta-se à vontade para enviar PRs com melhorias no código, como novos indicadores técnicos ou otimizações de coleta de dados.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
