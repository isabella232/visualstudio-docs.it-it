---
title: Estendibilità del servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulla struttura, l'implementazione e l'estensibilità dei servizi di linguaggio legacy in Visual Studio.
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
ms.workload:
- vssdk
ms.openlocfilehash: f22d6997d932884e5aeb8d794b7884b40a8d5dab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074496"
---
# <a name="legacy-language-service-extensibility"></a>Estendibilità dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce supporto specifico della lingua per la modifica del codice sorgente nell'IDE.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

 In questa sezione viene illustrata la struttura e l'implementazione di un servizio di linguaggio legacy.

## <a name="in-this-section"></a>Contenuto della sezione
- [Migrazione di un servizio di linguaggio legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.

- [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)

 Vengono fornite informazioni importanti su come sviluppare servizi di linguaggio per integrare un linguaggio di programmazione in Visual Studio.

- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)

 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Vengono fornite informazioni sul supporto dell'evidenziazione della sintassi in un servizio di linguaggio.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Vengono fornite informazioni su come utilizzare il Framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.

- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Vengono descritte le librerie e gli strumenti che consentono di esplorare le visualizzazioni ad albero dei simboli nell'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

 Viene fornita una panoramica degli editor di Visual Studio.

- [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)

 Vengono fornite informazioni su e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug dei programmi.
