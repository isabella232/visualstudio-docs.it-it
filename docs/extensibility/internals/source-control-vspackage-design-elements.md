---
title: Elementi di progettazione VSPackage del controllo del codice sorgente Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705004"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
Gli argomenti in questa sezione delineano la struttura che il controllo del codice sorgente VSPackage deve implementare per l'integrazione completa. Elenca inoltre le interfacce e i servizi che il controllo del codice sorgente VSPackage può [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementare e le interfacce e i servizi che il controllo del codice sorgente VSPackage può utilizzare da altri componenti per supportare il modello di controllo del codice sorgente e la funzionalità.

## <a name="in-this-section"></a>Contenuto della sezione
- [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definisce la struttura del controllo del codice sorgente VSPackage.

- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Elenca le interfacce e i servizi correlati al pacchetto del controllo del codice sorgente.

- [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Descrive il servizio di controllo del codice sorgente fornito dal controllo del codice sorgente VSPackage.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un controllo del codice sorgente VSPackage che non [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solo fornisce funzionalità di controllo del codice sorgente, ma può essere utilizzato per personalizzare l'interfaccia utente del controllo del codice sorgente.
