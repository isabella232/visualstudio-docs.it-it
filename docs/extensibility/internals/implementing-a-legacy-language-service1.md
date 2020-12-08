---
title: Implementazione di un oggetto Service1 del linguaggio legacy | Microsoft Docs
description: Informazioni su come implementare un servizio di linguaggio legacy che supporta le funzionalità del servizio di linguaggio esteso tramite il Framework di pacchetto gestito (MPF). Parte 1 di 2.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: be2caf25dfef71cb267f49b6cfd732923aa0848c
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761179"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementazione di un servizio di linguaggio Legacy 1
È possibile utilizzare le classi del Framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio legacy che supporta una vasta gamma di funzionalità, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e il completamento di IntelliSense.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)

 Panoramica delle funzionalità del servizio di linguaggio supportate in MPF.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Vengono descritti gli elementi necessari per implementare un servizio di linguaggio tramite MPF.

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Vengono descritti i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Vengono descritti i due parser necessari per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.

- [Procedura dettagliata: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Fornisce i passaggi di base necessari per implementare un servizio di linguaggio MPF in un VSPackage.

- [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Vengono illustrate le tecniche di recupero di un elenco di frammenti di codice installati.

- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)

 Vengono forniti collegamenti ad argomenti in cui vengono descritte le operazioni da eseguire per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.
