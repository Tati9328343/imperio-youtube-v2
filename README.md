# Imperio YouTube — Suite de herramientas IA (alternativa a Viani.pro)

Aplicación web **completa, funcional y 100% gratuita** que replica las funcionalidades públicas identificadas de [viani.pro](https://viani.pro/).

## 1. Inventario de funciones implementadas

| Herramienta     | Qué hace en esta app                                                                 | Estado |
|-----------------|--------------------------------------------------------------------------------------|--------|
| **Imperio Pro** | Genera guion completo + notas de escenas a partir de una idea/estilo/duración       | ✅ Funcional |
| **Rodri Pro**   | Informe de investigación de nicho: ideas de canales, videos virales, formatos       | ✅ Funcional |
| **Replica Pro** | Plan de réplica de un canal: análisis de estilo + 5 guiones nuevos + marca propia   | ✅ Funcional |
| **Agente Pro**  | Asesoría de canal + 5 ideas de próximos videos + guion listo del #1 recomendado     | ✅ Funcional |
| **Music Pro**   | Pack completo: títulos, descripción, letras, prompts Suno/Udio, escenas, tags       | ✅ Funcional |
| **Ebook Pro**   | Ebook completo (título, portada, capítulos, página de ventas) listo para PDF        | ✅ Funcional |
| **Miniatura Pro**| Genera 4 miniaturas con IA (Pollinations) a partir de título + estilo               | ✅ Funcional |
| Panel de control| Dashboard con acceso rápido a todas las herramientas + actividad reciente           | ✅ |
| Menú lateral    | Navegación completa + búsqueda de herramientas                                      | ✅ |
| Tema claro/oscuro| Soporte system / light / dark                                                       | ✅ |
| Historial       | Guarda hasta 200 ejecuciones en localStorage, permite ver/eliminar/exportar         | ✅ |
| Ajustes         | Configuración de tema + API key opcional de Groq                                    | ✅ |
| UI en español   | Toda la interfaz y resultados en español                                            | ✅ |
| Responsive      | Funciona en móvil, tablet y escritorio                                              | ✅ |

## 2. Funciones que NO pudieron reproducirse exactamente (y motivos)

| Función original (Viani)                  | Motivo de limitación                                                                 | Alternativa ofrecida |
|-------------------------------------------|--------------------------------------------------------------------------------------|----------------------|
| Video final renderizado (voz + imágenes + montaje) | Requiere GPU/servidores de pago o APIs costosas (Runway, Pika, ElevenLabs, etc.)    | Guion + notas de escenas listos para CapCut / DaVinci |
| Música generada y mezclada como DJ        | Generación de audio de calidad comercial no es gratuita a escala                    | Letras + prompts listos para Suno.ai / Udio (tier free) |
| Análisis en tiempo real de canales de YouTube | YouTube Data API tiene cuota limitada y requiere clave + proyecto Google            | Análisis basado en conocimiento del modelo + instrucciones para usar herramientas gratis |
| Miniaturas con texto editable integrado   | Pollinations genera la imagen; el texto exacto se añade después fácilmente          | Imágenes base + instrucciones para Canva/Photopea |
| Login de alumnos / panel privado de Viani | No es público; no hay acceso a su backend                                           | Historial local por navegador (sin cuentas) |

## 3. Cómo ejecutar el proyecto (local)

```bash
# 1. Clonar o entrar a la carpeta
cd imperio-youtube

# 2. Instalar dependencias
npm install

# 3. Arrancar en modo desarrollo
npm run dev
```

Abre http://localhost:5173

## 4. Cómo publicarlo gratis

### Opción recomendada: Vercel (cero costo)

1. Crea cuenta en [vercel.com](https://vercel.com) (gratis)
2. Instala Vercel CLI o conecta el repositorio GitHub
3. En la carpeta del proyecto:

```bash
npm i -g vercel
vercel
```

4. Sigue las preguntas (acepta defaults). En 1-2 minutos tendrás una URL pública tipo `https://imperio-youtube.vercel.app`

### Alternativas gratuitas

- **Netlify**: arrastra la carpeta `dist` después de `npm run build`
- **Cloudflare Pages**
- **GitHub Pages** (con configuración de base path)

No necesitas dominio de pago. La URL gratuita de Vercel/Netlify es suficiente.

## 5. Servicios utilizados y límites gratuitos

| Servicio              | Uso en la app                          | Plan gratuito                          | Notas |
|-----------------------|----------------------------------------|----------------------------------------|-------|
| **Pollinations.ai**   | Generación de miniaturas               | Sin API key, sin límites estrictos publicados | Puede tener rate limits ocasionales |
| **Groq (opcional)**   | Texto de alta calidad (Llama 3.1)      | Tier free generoso (tokens/día)        | Requiere registro en console.groq.com |
| **localStorage**      | Historial + ajustes + claves           | Limitado por el navegador (~5-10 MB)   | Se pierde si se limpia el caché |
| **Vite + React**      | Frontend                               | Open source                            | — |
| **Vercel / Netlify**  | Hosting                                | Plan hobby gratuito                    | Suficiente para uso personal |

## 6. Guía para configurar claves API

1. Ve a **Ajustes** en la app
2. (Opcional pero recomendado) Obtén una clave gratuita de Groq:
   - Entra a https://console.groq.com
   - Crea cuenta → API Keys → Create API Key
   - Copia la clave (`gsk_...`)
3. Pégala en el campo "Groq API Key" y pulsa Guardar
4. La clave **solo se guarda en tu navegador**. Nunca se envía a ningún servidor propio.

Sin clave la app sigue funcionando con generación local basada en plantillas inteligentes.

## 7. Pruebas realizadas

| Prueba                                      | Resultado |
|---------------------------------------------|-----------|
| Todas las rutas del menú abren              | ✅ |
| Formularios validan campos obligatorios     | ✅ |
| Generación de texto (modo local)            | ✅ |
| Generación de texto con Groq (si se configura) | ✅ |
| Generación de 4 miniaturas                  | ✅ |
| Guardado en historial y recuperación        | ✅ |
| Eliminación de registros y limpieza total   | ✅ |
| Cambio de tema claro/oscuro                 | ✅ |
| Búsqueda de herramientas en el menú         | ✅ |
| Botones Copiar / Descargar                  | ✅ |
| Responsive (móvil simulado)                 | ✅ |
| Persistencia tras recargar página           | ✅ |

## 8. Posibles costos futuros

- **Uso normal personal**: $0
- Si superas el rate limit de Pollinations o Groq free: puedes quedarte en modo local o esperar el reset diario.
- Si quieres generación real de video/audio a escala: habría que integrar servicios de pago (Runway, ElevenLabs, Suno Pro, etc.). La arquitectura permite añadirlos después sin reescribir todo.
- Dominio propio (.com / .co): opcional, desde ~$10-15 USD/año.

## Arquitectura técnica

- **Frontend**: React 18 + TypeScript + Vite + Tailwind CSS
- **Estado**: Zustand + persistencia en localStorage
- **Rutas**: React Router v6
- **IA texto**: Groq (Llama 3.1) opcional + fallback local robusto
- **IA imagen**: Pollinations.ai (sin key)
- **Sin backend propio**: todo corre en el navegador → hosting estático gratuito

## Estructura del código

```
src/
  components/     Layout, Sidebar, TopBar
  pages/          Dashboard, Historial, Ajustes
  tools/          Las 7 herramientas
  store/          Zustand store
  lib/            utils + capa de IA
  types/          TypeScript types
```

---

**Prioridad cumplida**: plataforma útil, segura, funcional y con costo operativo de **cero pesos colombianos**.
