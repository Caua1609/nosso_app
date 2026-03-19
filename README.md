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
```

# Fotos do Aplicativos
<img width="419" height="882" alt="image" src="https://github.com/user-attachments/assets/83234294-94dd-4136-98f6-fe3a0e87346b" />
<img width="367" height="782" alt="{3D215839-5B7D-48D9-AE54-F762B2235F71}" src="https://github.com/user-attachments/assets/9e372de7-3420-4764-98c5-a3f53cb85ad5" />
<img width="368" height="711" alt="{F1C6D7CD-7AEF-478E-A1D5-D052A0EF4FD0}" src="https://github.com/user-attachments/assets/1fbf7e32-1e03-44c3-a320-a47a9d96990f" />
<img width="357" height="701" alt="{32861FFE-2697-410B-A61C-72FA8AF6B289}" src="https://github.com/user-attachments/assets/cf0a8a57-95f9-4658-8971-1a99b77d28fc" />



