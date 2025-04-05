# 🚀 Postman Practice - API Test Collection

Coleção Postman para testes de API do sistema **Conduit** (plataforma de artigos/blog).

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

## 📌 Objetivo

Validar funcionalidades críticas do sistema através de:
- ✅ Testes de regressão
- 🔍 Validação de contratos API
- 🟢🔴 Cenários de sucesso e falha
- ⚠️ Edge cases (valores extremos/inválidos)

## 🧩 Funcionalidades Testadas

| Módulo       | Cenários                                                                 |
|--------------|--------------------------------------------------------------------------|
| **👤 Usuários** | Cadastro, Login, Atualização, Validação de campos, Credenciais inválidas|
| **📝 Artigos**  | CRUD, Feed Global, Tags, Autorizações                                    |
| **💬 Comentários**| Criação, Exclusão, Validação de permissões                             |
| **👥 Perfil**   | Seguir/Deixar de seguir, Visualização                                   |

## ⚙️ Pré-requisitos

- [Postman](https://www.postman.com/downloads/) instalado
- Acesso à API: `https://conduit.mate.academy/api/`
- Variáveis de ambiente configuradas:
  ```
  {
    "BASE_URL": "https://conduit.mate.academy/api/",
    "passwordConduit": "Deltapx7411!"
  }
  ```

## Como Usar

1. Importe a Coleção
2. Execute os Testes
  Abra cada requisição e:
  - Clique em Send para executar
  - Verifique os resultados na aba Test Results

3. Exemplo de Fluxo (Sign Up):
```
// Pré-request Script
let randomEmail = `user_${Math.floor(Math.random() * 10000)}@example.com`;
pm.variables.set("emailConduit", randomEmail);

// Testes Automatizados
pm.test("Status 200", () => pm.response.to.have.status(200));
pm.test("Resposta contém token", () => {
    pm.expect(pm.response.json().user).to.have.property("token");
});
```

## 🗂️ Estrutura dos Testes

- 📂 Coleção
  - 📂 User (18 cenários)
    - ✅ Success Sign Up
    - ❌ Sign Up com email inválido
    - ⚠️ Edge cases (username numérico, campos vazios)
  - 📂 Articles (15 cenários)
    - 📝 Create/Update
    - 🗑️ Delete/Validações
  - 📂 Profile (3 cenários)
    - 📝 Follow/Unfollow
  - 📂 Tags (1 cenário)
    - 📋 Get
  - 📂 Comments (5 cenários)
    - 💬 Post/Commentários
    - 🔒 Validação de permissões

## 💡 Dicas para Execução

1. Collection Runner para testes em massa:
```
newman run MinhaColecao.json
```

2. Monitoramento de variáveis:
```
View > Show Postman Console (Ctrl+Alt+C)
```

3. Debug de testes:
```
console.log("Dados da resposta:", pm.response.json());
```

## ⚠️ Observação
Muitos testes utilizam dados randômicos para evitar conflitos:
```
{{$randomEmail}}  // Exemplo de variável dinâmica
```

Feito com ❤️ por [Patrick Cavaleiro] | 🛠️ QA Engineer Junior
