---
title: Funzionalità vsPackage del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulle funzionalità di un VSPackage del controllo del codice sorgente, inclusi i dettagli di registrazione/selezione e su alcune delle principali funzionalità correlate al controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a2c3f44044b59502fc4a05ea511802179e382b00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034552"
---
# <a name="source-control-vspackage-features"></a>Funzionalità dei pacchetti VSPackage di controllo del codice sorgente
Questa sezione descrive le varie funzionalità di un VSPackage del controllo del codice sorgente. Illustra i dettagli di registrazione e selezione per un vspackage di questo tipo e illustra tre delle principali funzionalità correlate al controllo del codice sorgente: gestione degli eventi Query-Edit Query-Save (QEQS), sostituzione del glifo e interfaccia utente personalizzata per le funzioni di controllo del codice sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Descrive i meccanismi di registrazione e selezione del pacchetto.

- [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Illustra il ruolo degli eventi Query-Edit Query-Save e come vengono gestiti dal vsPackage del controllo del codice sorgente.

- [Controllo dei glifi](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Descrive i livelli di controllo degli glifi e come implementarli.

- [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Descrive gli elementi dell'interfaccia utente che un controllo del codice sorgente VSPackage può specificare.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce funzionalità di controllo del codice sorgente, ma può essere usato per personalizzare l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente del controllo del codice sorgente.
