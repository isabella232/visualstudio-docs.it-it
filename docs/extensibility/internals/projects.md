---
title: Progetti | Microsoft Docs
description: Informazioni sui modi in cui i pacchetti VSPackage possono estendere il Visual Studio di progetto, inclusi tipi di progetto, sottotipi di progetto e strumenti personalizzati.
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
ms.openlocfilehash: 9daeac1804940eb80331461b12b2cda51e9fef55
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636140"
---
# <a name="projects"></a>Progetti
In Visual Studio, i progetti sono i contenitori che gli sviluppatori usano per organizzare i file di codice sorgente e altre risorse visualizzate in **Esplora soluzioni**. In genere, i progetti sono file (ad esempio, un file con estensione csproj per un progetto C#) che archiviano riferimenti a file di codice sorgente e risorse come i file bitmap. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a database e servizi Web e altre risorse. I pacchetti VSPackage possono estendere il Visual Studio di progetto in tre modi *principali:* tipi di progetto, *sottotipi* di progetto e *strumenti personalizzati.*

## <a name="in-this-section"></a>Contenuto della sezione
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 *Project tipi aggiungono* il supporto per nuovi tipi di progetti, ad esempio i linguaggi di programmazione. Ad esempio, ogni linguaggio supportato Visual Studio ha un proprio tipo di progetto e l'esempio di integrazione IronPython include un tipo di progetto per il linguaggio IronPython. È necessario creare un tipo di progetto per linguaggi diversi da C# o Visual Basic per personalizzare la modalità di creazione, debug, distribuzione e visualizzazione degli elementi **in Esplora soluzioni**. Per altre informazioni, vedere [Tipi Project.](../../extensibility/internals/project-types.md)

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 *Project sottotipi* sono basati sui tipi di progetto e possono essere usati per personalizzare il modo in cui i progetti vengono compilati, debug e distribuiti. Visual Studio i sottotipi di progetto con i progetti smart device; personalizzano la distribuzione copiando un programma appena compilato da un computer di sviluppo nel dispositivo di destinazione. I tipi di progetto C# e Visual Basic possono essere usati come base per i sottotipi di progetto. I tipi di progetto C++ non possono. I tipi di progetto personalizzati possono essere usati anche come base per i sottotipi di progetto. Per altre informazioni, vedere [Project Subtypes](../../extensibility/internals/project-subtypes.md).

- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene illustrato il progetto Web, che a sua volta crea applicazioni Web.

- [New Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) and [New Project Generation: Under the Hood, Part Two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Spiega cosa accade effettivamente quando si crea un nuovo progetto.

- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene gli esempi in VSSDK che si occupano di progetti e soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [All'interno di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Illustrare i diversi aspetti Visual Studio estendibilità.
