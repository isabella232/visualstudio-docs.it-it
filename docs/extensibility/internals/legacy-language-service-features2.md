---
title: Features2 servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333498"
---
# <a name="legacy-language-service-features"></a>Funzionalità del servizio di linguaggio legacy
I seguenti argomenti elencano alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire.

 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.

## <a name="in-this-section"></a>In questa sezione
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare la colorazione della sintassi.

- [Formattazione automatica in un servizio di linguaggio legacy](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Viene illustrato come implementare la formattazione automatica.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene illustrato come implementare la descrizione comando informazioni sul parametro di IntelliSense.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'elenco di istruzioni di IntelliSense e l'elenco di completamento di membro.

- [Definizione della struttura e testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Viene illustrato come implementare il testo nascosto o della struttura.

- [Procedura: offrire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Illustra alcuni dei passaggi di implementazione di supporto del debugger...

## <a name="related-sections"></a>Sezioni correlate