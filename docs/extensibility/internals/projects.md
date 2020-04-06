---
title: Proprietà Projects . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706209"
---
# <a name="projects"></a>Progetti
In Visual Studio i progetti sono i contenitori utilizzati dagli sviluppatori per organizzare i file di codice sorgente e altre risorse visualizzate in **Esplora soluzioni.** In genere, i progetti sono file (ad esempio, un file con estensione csproj per un progetto C ) che archiviano i riferimenti ai file di codice sorgente e risorse come i file bitmap. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente, riferimenti a servizi Web e database e altre risorse. I package VS possono estendere il sistema di progetto di Visual Studio in tre modi principali: *tipi di progetto,* *sottotipi*di progetto e *strumenti personalizzati.*

## <a name="in-this-section"></a>Contenuto della sezione
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 *I tipi di progetto* aggiungono il supporto per nuovi tipi di progetti, ad esempio linguaggi di programmazione. Ad esempio, ogni linguaggio supportato da Visual Studio ha il proprio tipo di progetto e l'esempio di integrazione IronPython include un tipo di progetto per il linguaggio IronPython.For example, each language that Visual Studio supports has its own project type, and the IronPython integration sample includes a project type for the IronPython language. Per personalizzare la modalità di compilazione, debug, distribuzione e visualizzazione in **Esplora soluzioni,** è necessario creare un tipo di progetto per linguaggi diversi da C, Visual Basic o Visual Basic. Per ulteriori informazioni, vedere [Tipi di progetto](../../extensibility/internals/project-types.md).

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 *I sottotipi di* progetto sono basati sui tipi di progetto e possono essere utilizzati per personalizzare il modo in cui i progetti vengono compilati, sottoposti a debug e distribuiti. Visual Studio usa i sottotipi di progetto con i progetti Smart Device; personalizzano la distribuzione copiando un programma appena creato da un computer di sviluppo al dispositivo di destinazione. I tipi di progetto di C e Visual Basic possono essere utilizzati come base per i sottotipi di progetto; Non è possibile utilizzare i tipi di progetto Di C. I propri tipi di progetto possono essere utilizzati anche come base per i sottotipi di progetto. Per ulteriori informazioni, vedere [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene illustrato il progetto Web, che a sua volta crea applicazioni Web.

- Nuova generazione di [progetti: sotto il cofano, prima parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione di progetti: sotto il cofano, seconda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Viene illustrato ciò che si verifica effettivamente quando si crea un nuovo progetto.

- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene gli esempi in VSSDK che gestiscono progetti e soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [All'interno di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Spiegare diversi aspetti dell'estensibilità di Visual Studio.Explain different aspects of Visual Studio extensibility.
