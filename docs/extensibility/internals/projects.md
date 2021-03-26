---
title: Progetti | Microsoft Docs
description: Informazioni sulle modalità in cui i pacchetti VSPackage possono estendere il sistema di progetto di Visual Studio, inclusi i tipi di progetto, i sottotipi di progetto e gli strumenti personalizzati.
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
ms.workload:
- vssdk
ms.openlocfilehash: 73f685707d6c9f7a8b40bb57c5207c6a538fd1f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081022"
---
# <a name="projects"></a>Progetti
In Visual Studio i progetti sono i contenitori usati dagli sviluppatori per organizzare i file del codice sorgente e altre risorse visualizzate in **Esplora soluzioni**. In genere, i progetti sono file, ad esempio un file con estensione csproj per un progetto C#, che archiviano i riferimenti a file di codice sorgente e risorse come file bitmap. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente, riferimenti a servizi Web e database e altre risorse. I pacchetti VSPackage possono estendere il sistema di progetto di Visual Studio in tre modi principali: *tipi di progetto*, *sottotipi di progetto* e *strumenti personalizzati*.

## <a name="in-this-section"></a>Contenuto della sezione
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 I *tipi di progetto* aggiungono il supporto per nuovi tipi di progetti, ad esempio i linguaggi di programmazione. Ogni linguaggio supportato da Visual Studio, ad esempio, dispone di un proprio tipo di progetto e l'esempio di integrazione IronPython include un tipo di progetto per la lingua IronPython. È necessario creare un tipo di progetto per lingue diverse da C# o Visual Basic per personalizzare il modo in cui gli elementi vengono compilati, sottoposti a debug, distribuiti e visualizzati nel **Esplora soluzioni**. Per altre informazioni, vedere [tipi di progetto](../../extensibility/internals/project-types.md).

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 I *sottotipi di progetto* sono basati sui tipi di progetto e possono essere usati per personalizzare il modo in cui i progetti vengono compilati, sottoposti a debug e distribuiti. Visual Studio USA i sottotipi di progetto con i progetti Smart Device. personalizzano la distribuzione copiando un programma appena compilato da un computer di sviluppo al dispositivo di destinazione. I tipi di progetto C# e Visual Basic possono essere usati come base per i sottotipi di progetto; I tipi di progetto C++ non possono. I tipi di progetto personalizzati possono essere usati anche come base per i sottotipi di progetto. Per altre informazioni, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene illustrato il progetto Web, che a sua volta crea applicazioni Web.

- [Creazione di un nuovo progetto: dietro le quinte, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione di progetti: dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Spiega cosa accade effettivamente quando si crea un nuovo progetto.

- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene gli esempi in VSSDK che si occupano di progetti e soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [All'interno di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Illustrare diversi aspetti dell'estensibilità di Visual Studio.
