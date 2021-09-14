---
title: Implementazione di un servizio di linguaggio legacy1 | Microsoft Docs
description: Informazioni su come implementare un servizio di linguaggio legacy che supporta le funzionalità estese del servizio di linguaggio usando managed package framework (MPF). Parte 1 di 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: da7e2e78013b76045c162c95f9bad9ee78b1790b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710269"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementazione di un servizio di linguaggio legacy 1
È possibile usare le classi nel framework del pacchetto gestito (MPF) per implementare un servizio di linguaggio legacy che supporta un'ampia gamma di funzionalità, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e il completamento intelliSense.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)

 Panoramica delle funzionalità del servizio di linguaggio supportate in MPF.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Descrive gli elementi necessari per implementare un servizio di linguaggio tramite MPF.

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Descrive i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Descrive i due parser necessari per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.

- [Procedura dettagliata: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Vengono forniti i passaggi di base necessari per implementare un servizio di linguaggio MPF in un VSPackage.

- [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Illustra le tecniche di recupero di un elenco di frammenti di codice installati.

- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)

 Vengono forniti collegamenti ad argomenti che illustrano in dettaglio le procedure da eseguire per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.
