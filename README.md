# 🎓 Finanzas UDB - App Móvil de Gestión Financiera y Horario Estudiantil

<p align="center">
  <img src="./LOGO/logo.jpg" alt="Logo Finanzas UDB" width="180" style="border-radius: 20px;" />
</p>

<p align="center">
  <b>Aplicación móvil integral desarrollada con React Native y Expo para la comunidad universitaria de la Universidad Don Bosco (UDB).</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Expo-SDK%2054-000020?style=for-the-badge&logo=expo&logoColor=white" alt="Expo SDK 54" />
  <img src="https://img.shields.io/badge/React%20Native-0.81.5-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React Native" />
  <img src="https://img.shields.io/badge/Firebase-Firestore%20%26%20Auth-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/Platform-Android%20%7C%20iOS-brightgreen?style=for-the-badge&logo=android" alt="Platforms" />
  <img src="https://img.shields.io/badge/Offline-First%20Ready-blue?style=for-the-badge" alt="Offline Ready" />
</p>

---

## 📌 Descripción del Proyecto

**Finanzas UDB** es una solución móvil diseñada específicamente para cubrir las necesidades cotidianas de los estudiantes universitarios. Combina un **sistema robusto de administración de finanzas personales** (control de presupuestos, gastos, ingresos y metas de ahorro) con herramientas de apoyo académico: un **gestor de horario institucional con temporizador de próximas clases** y un agregador de **noticias oficiales en tiempo real de la Universidad Don Bosco (UDB)** con tolerancia y persistencia sin conexión (Offline-First).

Desarrollada como proyecto de cátedra para la materia de **Administración de Proyectos (Ciclo 4)**.

---

## 🚀 Características Principales

### 💰 1. Gestión de Finanzas Personales
- **Registro de Transacciones:** Clasificación rápida de ingresos y egresos por categorías (Alimentación, Transporte, Universidad/Matrícula, Materiales, Ocio, etc.).
- **Dashboard Estadístico:** Gráficas interactivas (`react-native-chart-kit` y SVG) con distribución porcentual de gastos, balance total y flujo mensual.
- **Control de Presupuestos:** Configuración de presupuestos por rubro con barra de progreso reactiva (`BudgetProgressBar`) y alertas visuales al superar límites.

### 📅 2. Horario Institucional Académico
- **Planificador Semanal de Materias:** Gestión de asignaturas, aulas, docentes, días y bloques de clase.
- **Cuenta Regresiva en Tiempo Real:** Algoritmo que calcula la proximidad de la siguiente clase ("EN BREVE", horas y minutos restantes) directamente en el Dashboard.
- **Notificaciones y Recordatorios:** Sincronización nativa de alertas de clase para no perder ningún laboratorio o sesión teórica.

### 📰 3. Noticias Institucionales UDB
- **Feed Oficial Actualizado:** Integración y consulta de comunicados oficiales y artículos del portal de la UDB (`https://www.udb.edu.sv`).
- **Caché y Modo Offline:** Motor de caché con `@react-native-async-storage/async-storage` y datos semilla de respaldo para acceso garantizado aun sin conexión a internet.

### 🌓 4. Experiencia de Usuario & Personalización
- **Tema Claro / Oscuro:** Selector dinámico de modo con persistencia automática del tema preferido.
- **Seguridad y Perfil:** Autenticación de usuarios vía Firebase Auth, protegiendo las finanzas de cada estudiante.
- **Sincronización en la Nube:** Conexión en tiempo real con Cloud Firestore para sincronización multidispositivo.

---

## 🛠️ Stack Tecnológico

| Capa / Módulo | Tecnología | Versión |
| :--- | :--- | :--- |
| **Framework Base** | [Expo SDK](https://expo.dev) | `~54.0.37` |
| **Entorno Móvil** | [React Native](https://reactnative.dev) | `0.81.5` |
| **Librería UI** | [React](https://react.dev) | `19.1.0` |
| **Navegación** | [React Navigation (Stack & Tabs)](https://reactnavigation.org) | `v7` |
| **Backend & Cloud** | [Firebase (Auth & Firestore)](https://firebase.google.com) | `^12.13.0` |
| **Almacenamiento Local**| [AsyncStorage](https://react-native-async-storage.github.io/async-storage/) | `^2.2.0` |
| **Gráficos & Visuales** | `react-native-chart-kit` & `react-native-svg` | `^6.12.2` / `15.12.1` |
| **Iconos & Componentes**| `@expo/vector-icons` (Ionicons), `@react-native-community/datetimepicker` | `^15.0.3` |
| **Compilación / Build**| Expo Application Services (EAS Build) | APK Release |

---

## 📂 Estructura del Proyecto

```text
FinanzasUDB/
├── APK/                        # Compilaciones ejecutables listas para Android (.apk)
├── assets/                     # Splash, íconos y logos adaptativos de la app
├── LOGO/                       # Recursos gráficos institucionales y logotipo
├── src/
│   ├── components/             # Componentes reutilizables (BudgetProgressBar, etc.)
│   ├── config/                 # Inicialización y configuración de Firebase SDK
│   ├── context/                # Proveedores de estado global (Auth, Finance, Theme)
│   ├── navigation/             # Enrutamiento y pilas (AppNavigator, Auth, Tabs)
│   ├── screens/                # Pantallas principales de la aplicación:
│   │   ├── LoginScreen.js      # Inicio de sesión seguro
│   │   ├── RegisterScreen.js   # Registro de nuevos estudiantes
│   │   ├── DashboardScreen.js  # Resumen financiero y widget de horario en vivo
│   │   ├── TransactionsScreen.js # Historial y creación de ingresos/gastos
│   │   ├── BudgetsScreen.js    # Presupuestos por categoría y límites de gasto
│   │   ├── ScheduleScreen.js   # Horario semanal institucional y materias
│   │   ├── NewsScreen.js       # Feed de noticias institucionales UDB
│   │   └── ProfileScreen.js    # Ajustes, tema y perfil de usuario
│   ├── services/               # Consumo de APIs externas y notificaciones
│   └── utils/                  # Ayudantes y referencias de navegación global
├── App.js                      # Punto de entrada y jerarquía de Context Providers
├── app.json                    # Configuración de Expo, plugins y metadata del paquete
├── eas.json                    # Perfiles de compilación EAS Build para Android
└── package.json                # Dependencias y scripts de ejecución
```

---

## ⚙️ Instalación y Puesta en Marcha

### Prerrequisitos
- [Node.js](https://nodejs.org/) (versión 18 o superior recomendada)
- Gestor de paquetes `npm` o `yarn`
- App móvil **Expo Go** instalada en tu dispositivo físico ([Android](https://play.google.com/store/apps/details?id=host.exp.exponent) o [iOS](https://apps.apple.com/app/expo-go/id982107779)) o un emulador configurado.

### Pasos

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/CesarMelendez698/AdministraciondeProyectos_FinanzasUDB.git
   cd AdministraciondeProyectos_FinanzasUDB
   ```

2. **Instalar dependencias:**
   ```bash
   npm install
   ```

3. **Iniciar el servidor de desarrollo:**
   ```bash
   npx expo start
   ```

4. **Ejecución en dispositivo:**
   - Escanea el código QR generado en la terminal con la cámara de tu teléfono (iOS) o desde la app Expo Go (Android).
   - O presiona `a` para abrir directamente en un emulador de Android conectado vía ADB.

---

## 📱 Descarga Directa del APK

Para probar la aplicación en un dispositivo Android sin necesidad de instalar entornos de desarrollo:
- Puedes encontrar el instalador listo en la carpeta [`APK/`](./APK/):
  - Archivo: `APK/application-d0e1ff3e-c46f-4ee2-9c31-7aebd6b33ef4.apk`
- Descarga el archivo en tu teléfono y habilita la instalación desde orígenes desconocidos para probarla de inmediato.

---

## 👥 Equipo de Desarrollo

Proyecto realizado en colaboración por:

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/CesarMelendez698">
        <img src="https://github.com/CesarMelendez698.png" width="100px;" alt="César Meléndez"/><br />
        <sub><b>César Meléndez</b></sub>
      </a><br />
      <sub>@CesarMelendez698</sub>
    </td>
    <td align="center">
      <a href="https://github.com/AlejandroFranco1101">
        <img src="https://github.com/AlejandroFranco1101.png" width="100px;" alt="Alejandro Franco"/><br />
        <sub><b>Alejandro Franco</b></sub>
      </a><br />
      <sub>@AlejandroFranco1101</sub>
    </td>
  </tr>
</table>

---

## 📄 Licencia

Este proyecto fue desarrollado con propósitos académicos para la **Universidad Don Bosco (UDB)**, El Salvador. Todos los derechos reservados © 2026.
