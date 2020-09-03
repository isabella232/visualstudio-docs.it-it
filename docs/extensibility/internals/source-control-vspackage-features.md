---
title: Funzionalità VSPackage del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a01b9d8fbf5f8d0645b5245d21b05aba9e7dacea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705022"
---
# <a name="source-control-vspackage-features"></a>Funzionalità dei pacchetti VSPackage di controllo del codice sorgente
Questa sezione descrive le varie funzionalità di un pacchetto VSPackage del controllo del codice sorgente. Vengono descritti i dettagli relativi alla registrazione e alla selezione per un pacchetto VSPackage e vengono illustrate tre delle principali funzionalità correlate al controllo del codice sorgente: gestione degli eventi di tipo Query-Save (QEQS), sostituzione di glifi e interfaccia utente personalizzata per le funzioni di controllo del codice sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Descrive i meccanismi di registrazione e selezione dei pacchetti.

- [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Viene illustrato il ruolo degli eventi di salvataggio delle query con modifiche di query e il modo in cui vengono gestiti dal pacchetto VSPackage del controllo del codice sorgente.

- [Controllo dei glifi](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Vengono descritti i livelli di controllo Glyph e come implementarli.

- [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Delinea gli elementi dell'interfaccia utente che possono essere specificati da un VSPackage del controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce la funzionalità del controllo del codice sorgente, ma può essere utilizzato per personalizzare l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente
