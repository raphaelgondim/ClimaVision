# 🌤 ClimaVision

> Dashboard de clima em tempo real com previsão de 7 dias, qualidade do ar e índice de conforto personalizado.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Open-Meteo](https://img.shields.io/badge/API-Open--Meteo-38BDF8?style=flat)
![Status](https://img.shields.io/badge/status-concluído-34D399?style=flat)

---

## 📋 Sobre o projeto

O **ClimaVision** é um dashboard meteorológico completo que permite consultar o clima de qualquer cidade do mundo em tempo real. O diferencial do projeto está no **Índice de Conforto**, um algoritmo próprio que combina temperatura, umidade e velocidade do vento para gerar uma recomendação em linguagem natural — algo que vai além de simplesmente exibir dados brutos.

O projeto foi desenvolvido com foco em boas práticas de consumo de APIs, manipulação dinâmica de DOM e visualização de dados, sem depender de nenhum framework.

---

## ✨ Funcionalidades

- 🔍 **Busca por qualquer cidade** via geocoding automático
- 🌡 **Clima atual** — temperatura real e sensação térmica
- 😊 **Índice de Conforto** — algoritmo próprio com recomendação em texto
- 📅 **Previsão de 7 dias** com mínima, máxima e condição do tempo
- 📊 **Gráfico de temperatura por hora** (hoje, com Chart.js)
- 💨 **Qualidade do ar** com barra visual de AQI e nível em PM2.5
- 🧭 **Bússola animada** com direção e velocidade do vento
- ☀️ **Nascer e pôr do sol** com duração total do dia
- 📱 **Totalmente responsivo** — funciona em mobile e desktop

---

## 🛠 Tecnologias

| Tecnologia | Uso |
|---|---|
| HTML5 | Estrutura semântica da interface |
| CSS3 | Layout (Grid/Flexbox), variáveis CSS, animações |
| JavaScript (ES6+) | Lógica, consumo de APIs, manipulação de DOM |
| [Chart.js](https://www.chartjs.org/) | Gráfico de temperatura por hora |
| [Open-Meteo](https://open-meteo.com/) | API de clima e previsão (sem chave) |
| [Open-Meteo Air Quality](https://open-meteo.com/en/docs/air-quality-api) | API de qualidade do ar (sem chave) |
| [Open-Meteo Geocoding](https://open-meteo.com/en/docs/geocoding-api) | Conversão de cidade → coordenadas |

> Todas as APIs são **gratuitas e não exigem cadastro ou chave de acesso**.

---

## 🚀 Como rodar

Não há instalação de dependências. O projeto roda direto no navegador.

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/climavision.git

# Abra o arquivo no navegador
cd climavision
open index.html
```

Ou simplesmente faça o download do `index.html` e abra com qualquer navegador moderno.

---

## 🧠 Algoritmo de conforto

O Índice de Conforto é calculado com base em três variáveis meteorológicas:

```javascript
function comfortIndex(temp, humidity, windSpeed) {
  let score = 100;

  // Temperatura ideal: 18–25°C
  if (temp < 10 || temp > 38) score -= 40;
  else if (temp < 15 || temp > 32) score -= 20;
  else if (temp < 18 || temp > 28) score -= 8;

  // Umidade ideal: 40–60%
  if (humidity > 85 || humidity < 20) score -= 30;
  else if (humidity > 70 || humidity < 30) score -= 15;

  // Vento
  if (windSpeed > 50) score -= 20;
  else if (windSpeed > 30) score -= 8;

  // Resultado
  if (score >= 80) return 'Ótimo para atividades ao ar livre';
  if (score >= 60) return 'Condições agradáveis hoje';
  if (score >= 40) return 'Conforto moderado — vista algo leve';
  return 'Evite exposição prolongada ao sol';
}
```

---

## 📁 Estrutura do projeto

```
climavision/
│
├── index.html
└── style.css   
└── README.md
```

---

## 🔭 Próximas melhorias

- [ ] Geolocalização automática ao carregar a página
- [ ] Histórico de cidades buscadas (localStorage)
- [ ] Modo claro / escuro com toggle
- [ ] Alertas meteorológicos
- [ ] Comparação entre duas cidades lado a lado

