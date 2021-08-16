---
title: Progetti | Microsoft Docs
description: Informazioni sui modi in cui i pacchetti VSPackage possono estendere il sistema Visual Studio progetto, inclusi tipi di progetto, sottotipi di progetto e strumenti personalizzati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2f0defdf43558cb94d3337a02d71ad768120da8c930244a9b03e1f05f6e75ee6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401284"
---
# <a name="projects"></a>Progetti
In Visual Studio, i progetti sono i contenitori che gli sviluppatori usano per organizzare i file di codice sorgente e altre risorse che vengono visualizzati in **Esplora soluzioni**. In genere, i progetti sono file (ad esempio, un file con estensione csproj per un progetto C#) che archiviano riferimenti a file di codice sorgente e risorse come file bitmap. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente, riferimenti a servizi Web e database e altre risorse. I pacchetti VSPackage possono estendere il Visual Studio di progetto in tre modi *principali:* tipi di *progetto,* sottotipi di progetto e *strumenti personalizzati.*

## <a name="in-this-section"></a>Contenuto della sezione
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 *Project tipi aggiungono* il supporto per nuovi tipi di progetti, ad esempio i linguaggi di programmazione. Ad esempio, ogni linguaggio supportato Visual Studio ha un proprio tipo di progetto e l'esempio di integrazione IronPython include un tipo di progetto per il linguaggio IronPython. È necessario creare un tipo di progetto per linguaggi diversi da C# o Visual Basic per personalizzare la modalità di creazione, debug, distribuzione e visualizzazione degli elementi **in** Esplora soluzioni . Per altre informazioni, vedere Tipi [Project .](../../extensibility/internals/project-types.md)

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 *Project sottotipi* sono basati sui tipi di progetto e possono essere usati per personalizzare il modo in cui i progetti vengono compilati, sottoprogetti e distribuiti. Visual Studio sottotipi di progetto con i progetti Smart Device; personalizzano la distribuzione copiando un programma appena compilato da un computer di sviluppo al dispositivo di destinazione. I tipi di progetto C# e Visual Basic possono essere usati come base per i sottotipi di progetto. I tipi di progetto C++ non possono. È anche possibile usare tipi di progetto personalizzati come base per i sottotipi di progetto. Per altre informazioni, vedere [sottotipi Project](../../extensibility/internals/project-subtypes.md).

- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene illustrato il progetto Web, che a sua volta crea applicazioni Web.

- [Nuova Project generazione: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [New Project Generation: Under the Hood, Part Two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Spiega cosa accade effettivamente quando si crea un nuovo progetto.

- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene gli esempi in VSSDK che si occupano di progetti e soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [All'interno di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Illustrare i diversi aspetti dell Visual Studio estendibilità.
