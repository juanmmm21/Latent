# Latent — El "Segundo Cerebro" Semántico 

**Latent** es un sistema de Gestión de Conocimiento Personal (PKM) *Local-First* centrado en la privacidad absoluta. A diferencia de las aplicaciones de notas tradicionales que dependen de carpetas rígidas o enlaces manuales, Latent utiliza Inteligencia Artificial local para estructurar tus pensamientos en un gráfico de conocimiento dinámico y permitirte interactuar con ellos mediante lenguaje natural.

>  **Privacidad Total:** Todo el procesamiento, desde la generación de embeddings vectoriales hasta la búsqueda y encriptación, se ejecuta de forma local en el dispositivo. Ningún byte de tus notas sale de tu iPhone o iPad.

---

##  Características Principales y Arquitectura Técnica

### 1. Búsqueda Vectorial Local y Chat Semántico (InferenceEngine) 
- **Procesamiento de Embeddings Local:** Integra un modelo de representación vectorial cuantizado (como `all-MiniLM-L6-v2`) convertido a **CoreML** (peso inferior a 50MB) para mapear textos a vectores de 384 dimensiones.
- **Background Tasks:** Las notas se vectorizan de forma asíncrona en segundo plano mediante las `.backgroundTask` de SwiftUI, garantizando que la escritura sea fluida y sin latencia.
- **Accelerate Framework (vDSP):** Para responder búsquedas semánticas al instante, se ejecuta la similitud de coseno sobre miles de vectores en paralelo utilizando instrucciones vectoriales SIMD de bajo nivel directamente en la CPU/GPU del dispositivo.

### 2. Base de Datos Modular y Híbrida (CoreDataLayer) 
- **SwiftData y CloudKit:** Sincronización automática a través de iCloud.
- **Relaciones Blandas (Soft Links):** Para evitar la saturación del motor de sincronización de CloudKit con miles de relaciones pequeñas, las notas implementan enlaces dinámicos mediante análisis de UUIDs en tiempo de ejecución.
- **Fusión Libre de Conflictos (CRDT):** Detección y fusión inteligente de conflictos en ediciones simultáneas sin conexión mediante el monitoreo de eventos de sincronización.

### 3. Seguridad de Nivel Fintech 
- **Cifrado en Reposo:** Todo el contenido de las notas se cifra de extremo a extremo utilizando **CryptoKit** (algoritmo ChaCha20-Poly1305).
- **Secure Enclave:** Las claves simétricas de encriptación se derivan y protegen utilizando el Secure Enclave del dispositivo mediante autenticación biométrica (Face ID / Touch ID) o el código de acceso.

### 4. Interfaz Premium e Interactiva (AppFeatureModules) 
- **Visualizador de Gráfico:** Renderizado interactivo de un gráfico dirigido por fuerzas (force-directed graph) implementado mediante **SwiftUI Canvas / Metal**, optimizado para renderizar cientos de nodos a **120Hz** sin caídas de frames.
- **Editor de Texto con TextKit 2:** Un editor de Markdown personalizado desarrollado envolviendo `UITextView` para un control total sobre el renderizado de enlaces dinámicos (wiki-links) y resaltado de sintaxis personalizado.

---

##  Stack Tecnológico

- **Lenguaje:** Swift 6 (Strict Concurrency)
- **UI:** SwiftUI, Metal, UIKit (TextKit 2)
- **Persistencia:** SwiftData, CloudKit
- **Matemáticas & IA:** CoreML, NaturalLanguage, Accelerate Framework (vDSP)
- **Criptografía:** CryptoKit, Security (Keychain)
- **Arquitectura:** Arquitectura Modular con Swift Package Manager (SPM)

---

##  Estructura del Proyecto

El proyecto está diseñado de forma modular para garantizar un bajo acoplamiento y facilitar el mantenimiento o la escalabilidad:

```
Latent/
├── Docs/                  # Documentación de diseño y especificaciones
├── LatentApp/             # Aplicación principal (iOS Wrapper e Interfaces principales)
└── Packages/              # Módulos de funcionalidad aislados (Swift Packages)
    ├── CoreDataLayer      # Persistencia, cifrado y CloudKit
    ├── InferenceEngine    # Envoltorio CoreML, tokenizador y motor matemático vDSP
    └── AppFeatureModules  # Módulos de UI (Editor, Visualizador de Gráfico, Búsqueda)
```

---

*Nota: Este repositorio público actúa como escaparate y documentación del diseño arquitectónico de la aplicación. El código fuente completo se mantiene en un repositorio privado de desarrollo.*
