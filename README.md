# SCI - Sistema de Controle de Insumos

Sistema completo para a gestão, acompanhamento, rastreio e movimentação de inventário. Essa aplicação foi desenhada para facilitar o fluxo de entradas e saídas e proporcionar agilidade utilizando leitura de QR Codes e registros fotográficos.

## 🚀 Módulos da Aplicação

O sistema é dividido nas seguintes telas principais:
1. **Inbound / Outbound** (`inbound_outbound.html`): Lançamento rápido de entradas de materiais, possibilitando upload de Excel em massa ou registro avulso com integração de câmera para laudo visual. Registro manual de saídas e geração de QRCodes das entradas.
2. **Expedição** (`expedicao.html`): Módulo desenvolvido para operadores de estoque, voltado para liberação rápida de materiais via escaneamento de QR Code pela câmera. Exige indicação de destino (Região/Estação).
3. **Inventário** (`inventario.html`): Dashboard executivo para visualização do saldo dos produtos em tempo real (Total Entrada - Total Saída). 
4. **Asset Management** (`asset.html`): Controle estrito do ciclo de vida de equipamentos e bens de alto valor (notebooks, monitores, etc.). Contempla controle por "Serial Number" (SN) e termo de comodato em formato PDF/Imagem.
5. **Visualização (Analytics)** (`visualizacao.html`): Retaguarda e administração. Permite pesquisa complexa de histórico, edição avulsa de registros incorretos, exclusão e exportação de tabelas completas em PDF.

## 🛠️ Tecnologias Utilizadas

A aplicação é executada 100% no navegador (*Client-Side*) e comunica-se com um BaaS (Backend as a Service):
* **Frontend UI**: HTML5, CSS3, JavaScript (ES6+), Bootstrap 5.3 e Tailwind CSS (somente na home).
* **Ícones & Estilos Adicionais**: FontAwesome 6, Google Fonts (Inter).
* **Alertas Dinâmicos**: SweetAlert2.
* **Leitura & Geração de QRCode**: html5-qrcode e qrcode.js.
* **Geração de Relatórios**: jsPDF e jsPDF-AutoTable.
* **Leitura de Planilhas Excel**: SheetJS (XLSX).
* **Banco de Dados Realtime**: Firebase Realtime Database.

## 🔧 Como Rodar o Projeto

Este projeto não exige uma build complexa com Node.js ou bundlers (como Webpack/Vite), pois importa bibliotecas via CDN. 
Para rodar:

1. Faça o clone ou baixe a pasta do repositório.
2. Devido a políticas de segurança CORS (especialmente no acesso de câmera e importação ES Modules no JavaScript), **você precisa rodar a aplicação através de um servidor local.**
3. Utilizando o VSCode:
   * Instale a extensão **Live Server**.
   * Clique com o botão direito no arquivo `index.html` e selecione **"Open with Live Server"**.
4. Acesse pelo seu navegador no endereço fornecido pelo Live Server (geralmente `http://127.0.0.1:5500`).

## 🔐 Acessos (Usuários de Demonstração)

A plataforma conta com um sistema customizado de proteção por "cargos". 
As seguintes credenciais de exemplo podem ser usadas para teste:

| Módulo             | Usuário       | Senha       | Permissão / Foco |
|--------------------|---------------|-------------|------------------|
| Inbound / Outbound | `inbound`     | `inbound123`| Gabriel          |
| Expedição          | `expedicao`   | `exp123`    | Rodrigo          |
| Inventário         | `inventario`  | `inv123`    | ERICLM           |
| Visualização       | `visualizacao`| `vis123`    | Mercia           |
| Asset              | `admin`       | `123456`    | ERICLM           |

> *As lógicas de login estão mapeadas no arquivo `acesso.js`.*

## ⚙️ Configuração do Banco de Dados

O arquivo `bd.js` realiza toda a camada de comunicação com o Firebase (API REST/SDK 10).
Caso deseje apontar para o seu próprio banco de dados, edite o bloco `firebaseConfig` presente no início do arquivo `bd.js`: