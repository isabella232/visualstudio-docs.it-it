---
title: Elementi di progettazione VSPackage del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705004"
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
