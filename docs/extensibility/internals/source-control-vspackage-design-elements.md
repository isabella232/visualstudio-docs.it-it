---
title: Elementi di progettazione VSPackage del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulla struttura che il pacchetto VSPackage del controllo del codice sorgente deve implementare e sulle interfacce e i servizi che il pacchetto VSPackage del controllo del codice sorgente può implementare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24a9b8dfa8036603c035a9112eb29688eab7ff25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852609"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
Negli argomenti di questa sezione viene illustrata la struttura che il pacchetto VSPackage del controllo del codice sorgente deve implementare per l'integrazione completa. Elenca inoltre le interfacce e i servizi che possono essere implementati dal pacchetto VSPackage del controllo del codice sorgente e le interfacce e i servizi che il pacchetto VSPackage del controllo del codice sorgente può utilizzare da altri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti per supportare il modello e la funzionalità del controllo del codice sorgente

## <a name="in-this-section"></a>Contenuto della sezione
- [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definisce la struttura del pacchetto VSPackage del controllo del codice sorgente.

- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Elenca i servizi e le interfacce correlate al pacchetto del controllo del codice sorgente.

- [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Descrive il servizio di controllo del codice sorgente fornito dal pacchetto VSPackage del controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce la funzionalità del controllo del codice sorgente, ma può essere utilizzato per personalizzare l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente
