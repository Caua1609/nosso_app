# 🌿 Leafy ♻️

![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-4285F4?style=for-the-badge&logo=android&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

O **Leafy** é um ecossistema mobile que une sustentabilidade e gamificação. Através de uma interface moderna em **Jetpack Compose**, o app engaja usuários em práticas ecológicas, recompensando ações positivas com XP e novos níveis de consciência ambiental.

---

## 📅 Log de Atualizações — Sprint 19/03

### 🏗️ Arquitetura e Core do App
Refatoramos a base do projeto para seguir as melhores práticas do Google:
* **Navigation Compose:** Implementação de `NavHost` com rotas tipadas para um fluxo de telas fluido.
* **Scaffold Central:** Gerenciamento global da interface, garantindo que a `BottomNavBar` esteja sempre acessível.
* **State Management:** Uso de `rememberNavController` e `currentBackStackEntryAsState` para persistência visual da aba ativa.

---

## 🚀 Funcionalidades Implementadas

### 🗺️ Sistema de Navegação & UI
* **BottomNavBar Customizada:** 5 pontos de entrada (`Início`, `Consultar`, `Scanner`, `Pontos`, `Educar`).
* **Identidade Visual:** Cores personalizadas com Verde Ativo (`#43A047`) e indicadores em Azul Claro (`#E6F2FF`).
* **Efeito Overlap:** Header verde fixo com degradê (`Brush.linearGradient`) que permanece sobre o conteúdo rolável.

### 🏠 Dashboard (Tela Início)
* **Card de Perfil:** Exibe avatar circular, nome do usuário e o nível atual (**Castor Engenheiro**).
* **Barra de Progresso:** Cálculo dinâmico de XP ($245 / 300$).
* **Estatísticas:** Grid de conquistas rápidas, dias seguidos de uso e total de contribuições.

### 🎮 Hub de Gamificação
* **Progressão de Níveis:** Sistema de 6 níveis, da *Formiga Operária* à *Fênix*.
* **Lógica de Bloqueio:** Feedback visual para níveis futuros com opacidade reduzida e ícones de cadeado.
* **Missões & Conquistas:** * Listagem de tarefas com badges de recompensa em verde.
    * Grid de conquistas otimizado com `chunked(2)` para exibição em duas colunas.

---

## 🛠️ Stack Técnica e Soluções de Performance

| Desafio | Solução | Benefício |
| :--- | :--- | :--- |
| **Rolagem de Tela** | `LazyColumn` | Substituiu o Column simples, evitando travamentos na UI. |
| **Ícones Faltantes** | `material-icons-extended` | Habilitou ícones específicos como `Eco` e `QrCodeScanner`. |
| **Layout Quebrado** | Ajuste de `contentPadding` | Garante que o conteúdo não seja "escondido" pelo Header fixo. |
| **Estabilidade** | Telas Placeholder | Evita crashes ao navegar para rotas ainda em desenvolvimento. |

---

## 🔧 Como Rodar o Projeto

Para garantir que todas as funcionalidades e ícones renderizem corretamente, adicione as seguintes dependências ao seu `build.gradle`:

```kotlin
dependencies {
    // Navegação
    implementation("androidx.navigation:navigation-compose:2.7.7")
    
    // Ícones Estendidos
    implementation("androidx.compose.material:material-icons-extended:1.6.0")
}
