# 🏥 ¿Quién quiere ser cardiólogo? - Competencia Interactiva

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![Firebase](https://img.shields.io/badge/Firebase-Realtime%20Database-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

> **Juego de competencia sobre miocardiopatías infiltrativas desarrollado para la Unidad Académica de Cardiología**
> 
> **Creado y Producido por: Rafael Mila**

Una aplicación web interactiva que permite a estudiantes y profesionales de cardiología competir en conocimientos sobre miocardiopatías infiltrativas, tanto de forma individual como por equipos.

## 🚀 Características Principales

### 🎮 Modalidades de Juego
- **🏆 Individual**: Competencia personal sin equipos
- **👥 Por Equipos**: Grupos A, B, C del foro de cardiología
- **🎯 30 Niveles**: Progresión de dificultad desde básico hasta experto
- **⏰ Tiempo Limitado**: 30 segundos por pregunta
- **💝 Sistema de Vidas**: 3 oportunidades por partida

### 📊 Sistema de Puntaje Avanzado
- **+1 punto** por respuesta correcta
- **+1 punto bonus** por respuesta rápida (≥20 segundos restantes)
- **+1 punto bonus** por niveles difíciles (20-30)
- **+3 puntos bonus** por racha de 5 respuestas correctas
- **+5 puntos bonus** por racha de 10 respuestas correctas
- **+10 puntos bonus** por completar los 30 niveles

### 🛠️ Funcionalidades Especiales
- **🎯 Comodín 50/50**: Elimina 2 opciones incorrectas
- **🔄 Cambiar Pregunta**: Obtiene una nueva pregunta del mismo nivel
- **📈 Rankings en Tiempo Real**: Individual y por equipos
- **🔔 Notificaciones Dinámicas**: Nuevos récords y cambios de liderazgo
- **👤 Jugadores Online**: Contador de usuarios conectados
- **📊 Analytics Completo**: Visitas, abandono, progreso

## 🛠️ Tecnologías Utilizadas

```javascript
Frontend: HTML5, CSS3, JavaScript (ES6+)
Backend: Firebase Realtime Database
Styling: CSS Grid, Flexbox, Custom Properties
Analytics: Firebase Analytics integrado
Security: Firebase Security Rules
```

## 📋 Instalación y Configuración

### Prerrequisitos
- Proyecto Firebase configurado
- Servidor web (local o hosting)
- Navegador web moderno

**Nota**: Para soporte en la configuración, contacta a Rafael Mila en r1000a@gmail.com

### 1. Obtener el Código
```bash
# Contactar a Rafael Mila en r1000a@gmail.com para obtener el código fuente
# O descargar desde la fuente oficial proporcionada

cd cardiologia-game
```

### 2. Configuración Firebase
```javascript
// Actualiza las credenciales en index.html línea 1150
const firebaseConfig = {
    apiKey: "tu-api-key",
    authDomain: "tu-proyecto.firebaseapp.com",
    databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com",
    projectId: "tu-proyecto-id",
    storageBucket: "tu-proyecto.firebasestorage.app",
    messagingSenderId: "tu-sender-id",
    appId: "tu-app-id"
};
```

**Importante**: Para obtener las credenciales Firebase del proyecto original, contacta a Rafael Mila en r1000a@gmail.com

### 3. Configurar Reglas de Seguridad
```json
{
  "rules": {
    "resultados": {
      ".read": true,
      ".write": "auth == null",
      "$resultId": {
        ".validate": "newData.hasChildren(['nombre', 'pseudonimo', 'cedula', 'grupo', 'puntaje', 'nivel']) && newData.child('puntaje').isNumber()"
      }
    },
    "gameStarts": {
      ".read": true,
      ".write": "auth == null"
    },
    "estadisticas": {
      ".read": true,
      ".write": "auth == null"
    },
    "analytics": {
      ".read": true,
      ".write": "auth == null"
    }
  }
}
```

### 4. Crear Banco de Preguntas
```bash
# Crear archivo questions_bank.json en la raíz
# Usar el formato del ejemplo proporcionado
```

### 5. Desplegar
```javascript
// Para servidor local
python -m http.server 8000
# o
npx serve .

# Para Firebase Hosting (contactar a Rafael Mila para configuración)
firebase deploy
```

**Soporte**: Para ayuda con el despliegue, contacta a Rafael Mila en r1000a@gmail.com

## 📁 Estructura del Proyecto

```
cardiologia-game/
├── index.html              # Aplicación principal
├── questions_bank.json     # Banco de preguntas
├── logo-ccu.png           # Logo Centro Cardiovascular
├── logo-uac.png           # Logo Unidad Académica
├── README.md              # Documentación
└── firebase.json          # Configuración Firebase (opcional)
```

## 🎯 Funcionalidades Detalladas

### 🏠 Dashboard Principal
- **📊 Estadísticas Generales**: Participantes, partidas, promedios
- **🥇 Ranking de Equipos**: Posiciones en tiempo real
- **🎮 Actividad Reciente**: Feed en vivo de resultados
- **👥 Jugadores Online**: Contador de usuarios conectados
- **📈 Visitas**: Contador total y diario

### 🏆 Sistema de Rankings
- **Individual**: Top 20 mejores puntajes únicos por jugador
- **Por Equipos**: Promedio de mejores puntajes por grupo
- **Modalidad Mixta**: Individual + Grupos en el mismo ranking

### 🔐 Panel de Administración
- **🔒 Acceso Protegido**: Contraseña: `cardio2025admin`
- **📋 Datos Completos**: Nombres reales, pseudónimos, cédulas
- **📥 Exportación**: Descarga en formato CSV
- **🗑️ Gestión de Datos**: Limpieza completa de registros
- **📊 Métricas de Abandono**: Partidas iniciadas vs completadas

### 🔔 Sistema de Notificaciones
```javascript
// Tipos de notificaciones automáticas:
✓ Nuevo récord individual establecido
✓ Cambio en el liderazgo de equipos
✓ Jugador inicia una nueva partida  
✓ Logros especiales desbloqueados
```

## 🎮 Cómo Jugar

### 1. Registro
- **Nombre y Apellido**: Para registros administrativos
- **Pseudónimo**: Aparece en rankings públicos (3-20 caracteres)
- **Cédula**: Validación sin dígito verificador (6-8 dígitos)
- **Modalidad**: Individual o Grupo A/B/C

### 2. Mecánica del Juego
- **30 Niveles Progresivos**: De estudiante a deidad cardiológica
- **30 Segundos por Pregunta**: Tiempo limitado
- **3 Vidas**: Tres errores y termina el juego
- **2 Comodines**: 50/50 y Cambiar Pregunta
- **2 Intentos por Jugador**: Máximo permitido

### 3. Progresión
```
Nivel 1-5:   Básico (Estudiante/Interno)
Nivel 6-10:  Intermedio (Residente/Fellow)
Nivel 11-15: Avanzado (Especialista)
Nivel 16-20: Experto (Referente)
Nivel 21-25: Maestro (Leyenda)
Nivel 26-30: Deidad (Olimpo Cardiológico)
```

## 📊 Base de Datos Firebase

### Estructura de Datos
```javascript
firebase-database/
├── resultados/              # Juegos completados
│   └── $resultId: {
│       nombre: string,
│       pseudonimo: string,
│       cedula: string,
│       grupo: string,
│       puntaje: number,
│       nivel: number,
│       fecha: string,
│       timestamp: number
│   }
├── gameStarts/              # Partidas iniciadas
│   └── $gameId: {
│       completed: boolean,
│       currentLevel: number,
│       currentScore: number
│   }
├── estadisticas/            # Métricas globales
│   ├── totalJugadores: number
│   ├── promedioScore: number
│   └── equipos: {
│       A: { players, avgScore, maxLevel },
│       B: { players, avgScore, maxLevel },
│       C: { players, avgScore, maxLevel },
│       INDIVIDUAL: { players, avgScore, maxLevel }
│   }
└── analytics/               # Analytics y tracking
    ├── totalVisits: number
    ├── dailyVisits/
    ├── visits/
    └── onlinePlayers/
```

## 🔒 Seguridad y Privacidad

### Datos Protegidos
- **Nombres Reales**: Solo visibles para administradores
- **Cédulas**: Únicamente para validar intentos únicos
- **Rankings Públicos**: Solo muestran pseudónimos
- **Acceso Admin**: Protegido por contraseña

### Validaciones
```javascript
// Frontend validations:
✓ Formato de cédula (6-8 dígitos numéricos)
✓ Pseudónimo alfanumérico (3-20 caracteres)
✓ Límite de 2 intentos por jugador
✓ Validación de grupos existentes

// Firebase Security Rules:
✓ Validación de tipos de datos
✓ Límites en valores numéricos  
✓ Prevención de escritura maliciosa
✓ Protección de rutas sensibles
```

## 📈 Analytics y Métricas

### Métricas Disponibles
- **Engagement**: Visitas vs Participaciones
- **Retención**: Partidas iniciadas vs completadas
- **Rendimiento**: Distribución de puntajes y niveles
- **Competencia**: Rankings y progresión temporal
- **Actividad**: Jugadores online en tiempo real

### Exportación de Datos
```csv
Fecha/Hora,Nombre Real,Pseudónimo,Cédula,Modalidad,Puntaje,Nivel,Intento
2025-01-15 10:30,Dr. Juan Pérez,CardioMaster,1234567,Grupo A,45,15,1
```

## 🛠️ Personalización

### Configuraciones Principales
```javascript
// Contraseña de administrador
const ADMIN_PASSWORD = "cardio2025admin";

// Sistema de puntaje
const SCORING_SYSTEM = {
    BASE_POINTS: 1,
    TIME_BONUS_THRESHOLD: 20,
    TIME_BONUS_POINTS: 1,
    HARD_LEVEL_THRESHOLD: 20,
    HARD_LEVEL_BONUS: 1,
    STREAK_BONUS_5: 3,
    STREAK_BONUS_10: 5,
    PERFECT_GAME_BONUS: 10
};

// Límites del juego
const MAX_ATTEMPTS = 2;
const TIMER_SECONDS = 30;
const TOTAL_LEVELS = 30;
```

### Agregar Preguntas
```json
{
    "id": "infiltrativas_031",
    "level": 16,
    "question": "Nueva pregunta sobre miocardiopatías infiltrativas",
    "options": [
        {"text": "Opción correcta", "correct": true},
        {"text": "Opción incorrecta 1", "correct": false},
        {"text": "Opción incorrecta 2", "correct": false},
        {"text": "Opción incorrecta 3", "correct": false}
    ]
}
```

## 🐛 Resolución de Problemas

### Problemas Comunes

#### No cargan las preguntas
```bash
# Verificar ubicación del archivo
ls questions_bank.json

# Validar JSON
node -p "JSON.parse(require('fs').readFileSync('questions_bank.json'))"
```

#### Firebase no conecta
```javascript
// Verificar credenciales en console.log
console.log('Firebase config:', firebaseConfig);

// Revisar reglas de seguridad
// Verificar permisos de escritura anónima
```

#### Notificaciones no aparecen
```javascript
// Verificar en consola del navegador
console.log('Notification system:', document.getElementById('liveNotifications'));

// Verificar conexión tiempo real
database.ref('resultados').on('value', snap => console.log('Data updated'));
```

## 🤝 Contribución

Este proyecto es obra de **Rafael Mila**. Para contribuciones, mejoras o colaboraciones:

### Cómo Contribuir
1. Contacta a Rafael Mila en r1000a@gmail.com
2. Propón mejoras o nuevas funcionalidades
3. Reporta bugs o problemas encontrados
4. Sugiere contenido médico adicional

### Estándares de Código
- Usar ES6+ JavaScript
- Comentarios en español para el contexto médico
- Validación de entrada en frontend y backend
- Responsive design para móviles

**Nota**: Este es un proyecto educativo especializado. Todas las contribuciones de contenido médico deben ser validadas por profesionales en cardiología.

## 📊 Roadmap

### Versión 2.1 (Próxima)
- [ ] Sistema de logros expandido
- [ ] Modo torneo con períodos específicos
- [ ] Análisis de preguntas más difíciles
- [ ] Notificaciones push

### Versión 2.2 (Futuro)
- [ ] Integración con calendario académico
- [ ] Multiplayer en tiempo real
- [ ] Sistema de badges y certificaciones
- [ ] API pública para integraciones

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

**Copyright (c) 2025 Rafael Mila**

## 👨‍⚕️ Créditos

**Creado y Producido por:**
- **Rafael Mila** - Desarrollador Principal y Creador del Proyecto

**Desarrollado para:**
- Centro Cardiovascular Universitario
- Unidad Académica de Cardiología

**Especialidad:** Miocardiopatías Infiltrativas
**Versión:** 2.0.0
**Año:** 2025

---

## 📞 Soporte

Para soporte técnico, preguntas sobre el contenido médico, o consultas sobre el proyecto:
- 📧 **Email**: r1000a@gmail.com
- 🐛 Reportar problemas: Escribir a r1000a@gmail.com
- 📚 Documentación: Contactar al desarrollador para información adicional

**Desarrollador**: Rafael Mila

---

> *"Un proyecto educativo diseñado para hacer más atractivo y competitivo el aprendizaje de las miocardiopatías infiltrativas."* - Rafael Mila

**¡Que comience la competencia cardiológica! 🏆❤️**