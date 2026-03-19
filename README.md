# Leafy ♻️

## Resumo do que foi feito - Dia 19/03

### Configuração inicial ⚙️
A MainActivity original tinha problemas sérios: um Surface vazio, um Box com innerPadding solto que não fazia nada, e nenhuma navegação configurada. Refizemos ela do zero adicionando o NavHost com rememberNavController para gerenciar toda a navegação, e o Scaffold com bottomBar para exibir a barra de navegação inferior em todas as telas. Também adicionamos a dependência navigation-compose no build.gradle para habilitar a navegação entre telas.

### Sistema de navegação ✈️
Usamos o Jetpack Navigation for Compose, que é a abordagem moderna recomendada pelo Google. Cada tela tem uma rota em texto simples como "home" e "gamificacao". Para navegar usamos navController.navigate("rota"), e para voltar usamos navController.popBackStack(). O popUpTo com saveState e restoreState preserva o estado das telas ao trocar de aba. A tela de Gamificação é uma sub-rota do Início, então a aba Início permanece selecionada quando o usuário está nela.

### BottomNavBar ▶️
Criamos o componente BottomNavBar.kt separado e reutilizável, com os 5 botões: Início, Consultar, Scanner, Pontos e Educar. Ele usa currentBackStackEntryAsState() para detectar a rota ativa e colorir o ícone correto de verde com o indicador. As cores foram personalizadas: ícone ativo verde 0xFF43A047, fundo do indicador azul claro 0xFFE6F2FF, e ícones inativos cinza.

### Tela Início 📲
A TelaInicio.kt foi construída com quatro partes principais. O header usa Brush.linearGradient para criar o degradê verde com o logo e slogan do app. O CardPerfil exibe a foto do usuário recortada em círculo com CircleShape, o nome, a data de membro, o avatar do nível Castor Engenheiro, a barra de progresso XP calculada como 245f / 300f com cor amarela, e as três estatísticas de conquistas, dias seguidos e contribuições. Os CardAcaoRapida são componentes reutilizáveis que recebem ícone, título, subtítulo e um onClick para navegar para a tela correspondente. O botão "Ver Tudo" navega para a rota "gamificacao". Trocamos o Column simples por LazyColumn para que o conteúdo role suavemente sem travar o app.

### Tela Gamificação 🎮
A TelaGamificacao.kt é acessada pelo botão "Ver Tudo" e tem cinco seções. O CardNivelAtual mostra o avatar do Castor, o nome e descrição do nível em itálico roxo, e a barra de progresso com 73% sobreposto usando um Box com align(Alignment.Center). O CardSequenciaDiaria exibe os 7 dias consecutivos com o incentivo de ganhar +20 XP por dia. A SecaoGanheXP lista as quatro tarefas disponíveis com seus bônus exibidos em badges verdes arredondados. A SecaoNiveis mostra os seis níveis do app — Formiga Operária, Castor Engenheiro, Lobo Guardião, Condor dos Andes, Tartaruga Milenar e Fênix — com lógica condicional: o nível atual tem borda roxa e badge ATUAL, os bloqueados mostram cadeado cinza e texto apagado. A SecaoConquistas usa chunked(2) para criar automaticamente o grid de duas colunas sem precisar de LazyVerticalGrid, exibindo emoji para conquistas desbloqueadas e cadeado para as bloqueadas, com a data de conclusão em verde.

### Efeito de sobreposição do header 🚀
Para criar o efeito do header verde fixo por cima do conteúdo rolável, trocamos o Column raiz por um Box. O LazyColumn fica declarado primeiro, ou seja, por baixo e o header verde fica declarado depois, ficando por cima. O contentPadding(top = 110.dp) empurra o primeiro item da lista para baixo do header. Usamos heightIn(min = 72.dp) para garantir que os headers das duas telas tenham a mesma altura. O botão de voltar usa Icons.Default.ArrowBack alinhado à esquerda com Alignment.CenterStart e chama navController.popBackStack() ao ser clicado.
Problemas resolvidos ao longo do caminho

Removemos o Surface e Box soltos que quebravam o layout inicial. Corrigimos os ícones Icons.Default.Eco e Icons.Default.QrCodeScanner que não existem no pacote básico do Material Icons, resolvendo com a adição do pacote material-icons-extended ou substituindo por ícones equivalentes disponíveis. Corrigimos o contentPadding = PaddingValues(all = 16.dp) que não deixava espaço para o header verde e o conteúdo ficava escondido atrás dele. Criamos telas placeholder para TelaConsultar, TelaScanner, TelaPontos e TelaEducar para evitar erros de compilação enquanto as telas reais não estão implementadas.
