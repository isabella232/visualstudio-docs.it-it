---
title: Determinare se implementare un controllo del codice sorgente VSPackage. Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708727"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinare se implementare un controllo del codice sorgente VSPackageDetermine whether to implement a source control VSPackage
In questa sezione vengono elaborate le scelte dei plug-in del controllo del codice sorgente e VSPackage del controllo del codice sorgente per estendere le soluzioni di controllo del codice sorgente e vengono fornite linee guida generali sulla scelta di un percorso di integrazione adatto.

## <a name="small-source-control-solution-with-limited-resources"></a>Soluzione di controllo del codice sorgente di piccole dimensioni con risorse limitate
 Se si dispone di risorse limitate e non è possibile essere gravato con l'overhead di scrittura di un pacchetto di controllo del codice sorgente, è possibile creare plug-in basati su API controllo del codice sorgente. Per ulteriori informazioni, consultate [Registrazione e selezione.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Soluzione di controllo del codice sorgente di grandi dimensioni con un set di funzionalità avanzateLarge source control solution with a rich feature set
 Se si desidera implementare una soluzione di controllo del codice sorgente che fornisce un modello di controllo del codice sorgente completo che non viene acquisito in modo adeguato utilizzando l'API plug-in del controllo del codice sorgente, è possibile considerare un pacchetto di controllo del codice sorgente come percorso di integrazione. Ciò si applica soprattutto se si preferisce sostituire il pacchetto dell'adattatore del controllo del codice sorgente (che comunica con i plug-in del controllo del codice sorgente e fornisce un'interfaccia utente del controllo del codice sorgente di base) con il proprio in modo che è possibile gestire gli eventi del controllo del codice sorgente in modo personalizzato. Se si dispone già di un'interfaccia utente del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]controllo del codice sorgente soddisfacente e si desidera mantenere tale esperienza in , l'opzione del pacchetto del controllo del codice sorgente consente di eseguire questa operazione. Il pacchetto del controllo del codice sorgente non [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è generico ed è progettato esclusivamente per l'utilizzo con IDE.

 Se si desidera implementare una soluzione di controllo del codice sorgente che offre flessibilità e un controllo più completo sulla logica e sull'interfaccia utente del controllo del codice sorgente, è possibile preferire la route di integrazione del pacchetto del controllo del codice sorgente. È possibile:

1. Registrare il proprio controllo del codice sorgente VSPackage (vedere [Registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata (vedere [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Specificate i glifi da utilizzare e gestite gli eventi glifo di Esplora soluzioni (consultate [Controllo glifi).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Gestire gli eventi Modifica query e Salvataggio query (vedere [Salvataggio modifica query).](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

## <a name="see-also"></a>Vedere anche
- [Creare un plug-in del controllo del codice sorgenteCreate a source control plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)
