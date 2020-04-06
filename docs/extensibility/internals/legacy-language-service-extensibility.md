---
title: Estensibilità del servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707414"
---
# <a name="legacy-language-service-extensibility"></a>Estendibilità dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce il supporto specifico del linguaggio per la modifica del codice sorgente nell'IDE.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

 In questa sezione vengono illustrate la struttura e l'implementazione di un servizio di linguaggio legacy.

## <a name="in-this-section"></a>Contenuto della sezione
- [Migrazione di un servizio di linguaggio legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.

- [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)

 Vengono fornite informazioni importanti sullo sviluppo di servizi di linguaggio per integrare un linguaggio di programmazione in Visual Studio.

- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)

 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Vengono fornite informazioni sul supporto dell'evidenziazione della sintassi in un servizio di linguaggio.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Vengono fornite informazioni su come utilizzare il framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.

- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Vengono descritte le librerie e gli strumenti che consentono di esplorare le visualizzazioni struttura ad albero dei simboli nell'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

 Viene fornita una panoramica degli editor di Visual Studio.Provides an overview of Visual Studio editors.

- [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)

 Fornisce informazioni su e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug dei programmi.
