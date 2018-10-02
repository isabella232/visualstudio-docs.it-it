---
title: Per determinare se implementare un VSPackage di controllo del codice sorgente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2af76d97b9fcf725079593155f8c3c5f695ca50a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530807"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Scelta di implementazione di un pacchetto VSPackage di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Determining Whether per implementare un VSPackage di controllo del codice sorgente](https://docs.microsoft.com/visualstudio/extensibility/internals/determining-whether-to-implement-a-source-control-vspackage).  
  
In questa sezione vengono illustrate le scelte di plug-in controllo codice sorgente e controllo del codice sorgente pacchetti VSPackage per estendere le soluzioni e fornisce indicazioni generali sulla scelta di un percorso adatto integrazione controllo del codice sorgente.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Soluzione di controllo di origine di dimensioni ridotte con risorse limitate  
 Se si hanno risorse limitate e non può essere sovraccaricato con l'overhead della scrittura di un pacchetto controllo del codice sorgente, è possibile creare plug-in basato su API dei plug-in del controllo origine. In questo modo è possibile usare affiancato con i pacchetti del controllo origine e possono passare tra plug-in controllo codice sorgente e i pacchetti su richiesta. Per altre informazioni, vedere [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Soluzione di controllo sorgente di grandi dimensioni con un Set di funzionalità avanzate  
 Se si desidera implementare una soluzione di controllo di origine che fornisce un modello di controllo di origine completo che non verrà acquisito in modo adeguato utilizzando l'API dei plug-in del controllo origine, è possibile considerare un pacchetto del controllo sorgente come percorso di integrazione. Questo vale in particolare se invece si sostituirà il pacchetto di scheda di controllo codice sorgente, che comunica con i plug-in controllo codice sorgente e fornisce un controllo di origine di base dell'interfaccia utente, con i propri in modo che è possibile gestire gli eventi di controllo di origine in modo personalizzato. Se si ha già un'origine soddisfacente controllo dell'interfaccia utente e per mantenere tale esperienza acquisita in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l'opzione del pacchetto controllo origine consente di farlo. Il pacchetto del controllo codice sorgente non è generico ed è progettato esclusivamente per l'uso con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Se si desidera implementare una soluzione di controllo di origine che fornisce la flessibilità e controllo più completo tramite l'interfaccia utente e la logica di controllo di origine, è preferibile la route di integrazione origine pacchetto controllo. È possibile:  
  
1.  Registrare il proprio controllo del codice sorgente VSPackage (vedere [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Sostituire il controllo del codice sorgente predefinite dell'interfaccia utente con l'interfaccia utente personalizzata (vedere [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Specificare i glifi da utilizzare e gestire gli eventi del glifo di Esplora soluzioni (vedere [controllo Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Gestire gli eventi di Query modificare e salvare Query (vedere [salvataggio delle Query Edit Query](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)

