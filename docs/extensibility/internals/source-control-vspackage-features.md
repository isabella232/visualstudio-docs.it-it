---
title: Funzionalità VSPackage del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulle funzionalità di un pacchetto VSPackage del controllo del codice sorgente, inclusi i dettagli di registrazione/selezione e su alcune delle principali funzionalità correlate al controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd501aa6d1fc3189d5008d76deb56dd570d03d8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064124"
---
# <a name="source-control-vspackage-features"></a>Funzionalità dei pacchetti VSPackage di controllo del codice sorgente
Questa sezione descrive le varie funzionalità di un pacchetto VSPackage del controllo del codice sorgente. Vengono descritti i dettagli di registrazione e selezione per un pacchetto VSPackage e vengono illustrate tre delle principali funzionalità correlate al controllo del codice sorgente: gestione degli eventi Query-Edit Query-Save (QEQS), sostituzione di glifi e interfaccia utente personalizzata per le funzioni di controllo del codice sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Descrive i meccanismi di registrazione e selezione dei pacchetti.

- [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Viene illustrato il ruolo degli eventi Query-Edit Query-Save e il modo in cui vengono gestiti dal pacchetto VSPackage del controllo del codice sorgente.

- [Controllo dei glifi](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Vengono descritti i livelli di controllo Glyph e come implementarli.

- [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Delinea gli elementi dell'interfaccia utente che possono essere specificati da un VSPackage del controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce la funzionalità del controllo del codice sorgente, ma può essere utilizzato per personalizzare l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente
