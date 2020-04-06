---
title: Implementazione di un servizio di linguaggio Legacy1 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707690"
---
# <a name="implementing-a-legacy-language-service"></a>Implementazione di un servizio di linguaggio legacy
È possibile utilizzare le classi nel framework del pacchetto gestito (MPF) per implementare un servizio di linguaggio legacy che supporta un'ampia gamma di funzionalità, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e il completamento di IntelliSense.You can use classes in the managed package framework (MPF) to implement a legacy language service that supports a wide variety of features, such as syntax highlighting, brace matching, and IntelliSense completion.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)

 Panoramica delle funzionalità del servizio di linguaggio supportate in MPF.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Vengono descritti gli elementi necessari per implementare un servizio di linguaggio tramite MPF.

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Vengono descritti i passaggi necessari per registrare un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]servizio di linguaggio basato su MPF con .

- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Vengono descritti i due parser necessari per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.

- [Procedura dettagliata: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Vengono eseguiti i passaggi di base necessari per implementare un servizio di linguaggio MPF in un pacchetto VSPackage.

- [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Vengono illustrate le tecniche di recupero di un elenco di frammenti di codice installati.

- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)

 Vengono forniti collegamenti ad argomenti che illustrano in dettaglio le operazioni da eseguire per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.
