---
title: Funzionalità del servizio di linguaggio Legacy2 - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f12e816476aa54f334988b99b9e86e820784f6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707364"
---
# <a name="legacy-language-service-features"></a>Funzionalità dei servizi di linguaggio legacy
Negli argomenti seguenti sono elencate alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare la colorazione della sintassi.

- [Formattazione automatica in un servizio di linguaggio legacy](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Viene illustrato come implementare la formattazione automatica.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene illustrato come implementare la descrizione comando informazioni sul parametro IntelliSense.Explains how to implement the IntelliSense Parameter Info Tooltip.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'elenco di istruzioni IntelliSense e l'elenco di completamento dei membri.

- [Definizione della struttura e testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Viene illustrato come implementare la struttura o il testo nascosto.

- [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrati alcuni passaggi per l'implementazione del supporto del debugger.

## <a name="related-sections"></a>Sezioni correlate
