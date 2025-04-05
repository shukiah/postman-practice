# Postman Practice - API Test Collection

Coleção Postman para testes de API do sistema **Conduit** (plataforma de artigos/blog), desenvolvida por Patrick Cavaleiro.

## Objetivo
Validar funcionalidades críticas do sistema através de:
- Testes de regressão
- Validação de contratos API
- Cenários de sucesso e falha
- Edge cases (valores extremos/inválidos)

## Funcionalidades Testadas
| Módulo       | Cenários                                                                 |
|--------------|--------------------------------------------------------------------------|
| **Usuários** | Cadastro, Login, Atualização, Validação de campos, Credenciais inválidas|
| **Artigos**  | CRUD, Feed Global, Tags, Autorizações                                    |
| **Comentários**| Criação, Exclusão, Validação de permissões                             |
| **Perfil**   | Seguir/Deixar de seguir, Visualização                                   |

## Pré-requisitos
- [Postman](https://www.postman.com/downloads/) instalado
- Acesso à API: `https://conduit.mate.academy/api/`
- Variáveis de ambiente configuradas:
  ```json
  {
    "BASE_URL": "https://conduit.mate.academy/api/",
    "passwordConduit": "Deltapx7411!"
  }

  Como Usar
Importe a Coleção

# Faça o download do arquivo .json
git clone https://github.com/seu-usuario/seu-repositorio.git

Execute os Testes
Abra cada requisição e:

Clique em Send para executar

Verifique os resultados na aba Test Results

Exemplo de Fluxo (Sign Up):

// Pré-request Script
let randomEmail = `user_${Math.floor(Math.random() * 10000)}@example.com`;
pm.variables.set("emailConduit", randomEmail);

// Testes Automatizados
pm.test("Status 200", () => pm.response.to.have.status(200));
pm.test("Resposta contém token", () => {
    pm.expect(pm.response.json().user).to.have.property("token");
});

Estrutura dos Testes

📂 Coleção
├─ 📂 User (18 cenários)
│  ├✅ Success Sign Up
│  ├❌ Sign Up com email inválido
│  └⚠️ Edge cases (username numérico, campos vazios)
├─ 📂 Articles (15 cenários)
│  ├📝 Create/Update
│  └🗑️ Delete/Validações
└─ 📂 Comments (5 cenários)
   ├💬 Post/Commentários
   └🔒 Validação de permissões

   Dicas para Execução
Use o Collection Runner para testes em massa:

newman run MinhaColecao.json

Monitore variáveis no console:

View > Show Postman Console (Ctrl+Alt+C)

Para debugar testes:

console.log("Dados da resposta:", pm.response.json());

Observação: Dados randômicos são usados para evitar conflitos (ex: {{$randomEmail}}).

Feito com ❤️ por Patrick Cavaleiro | QA Engineer Jr 