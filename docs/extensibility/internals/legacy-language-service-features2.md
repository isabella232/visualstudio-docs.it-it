---
title: Funzionalità del servizio di linguaggio legacy2 | Microsoft Docs
description: Informazioni su alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire usando le estensioni di Managed Extensibility Framework (MEF) in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 11305d2a63b2e461629302e4a9bf88ed6d7c21b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049831"
---
# <a name="legacy-language-service-features-2"></a>Funzionalità del servizio di linguaggio legacy 2
Negli argomenti seguenti sono elencate alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare la colorazione della sintassi.

- [Formattazione automatica in un servizio di linguaggio legacy](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Viene illustrato come implementare la formattazione automatica.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene illustrato come implementare la descrizione comando delle informazioni sui parametri di IntelliSense.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'elenco di istruzioni IntelliSense e l'elenco di completamento dei membri.

- [Definizione della struttura e testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Viene illustrato come implementare la struttura o il testo nascosto.

- [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrati alcuni dei passaggi per l'implementazione del supporto del debugger.

## <a name="related-sections"></a>Sezioni correlate
