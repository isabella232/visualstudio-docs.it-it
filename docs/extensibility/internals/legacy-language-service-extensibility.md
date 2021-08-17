---
title: Estendibilità del servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulla struttura, l'implementazione e l'estendibilità dei servizi di linguaggio legacy in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e492dbae044b5051fc4de9178da981003735d24b3b0e37ba944a99aa6dd4a125
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375871"
---
# <a name="legacy-language-service-extensibility"></a>Estendibilità dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce supporto specifico del linguaggio per la modifica del codice sorgente nell'IDE.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

 Questa sezione illustra la struttura e l'implementazione di un servizio di linguaggio legacy.

## <a name="in-this-section"></a>Contenuto della sezione
- [Migrazione di un servizio di linguaggio legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.

- [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)

 Fornisce informazioni importanti su come sviluppare servizi di linguaggio per integrare un linguaggio di programmazione Visual Studio.

- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)

 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Vengono fornite informazioni sul supporto dell'evidenziazione della sintassi in un servizio di linguaggio.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornisce informazioni su come usare il framework del pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.

- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Vengono descritte le librerie e gli strumenti che consentono di esplorare le visualizzazioni albero dei simboli nell'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

 Fornisce una panoramica degli Visual Studio editor.

- [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)

 Fornisce informazioni su e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger usati per il debug dei programmi.
