---
title: Origine controllo integrazione Essentials | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9893d5525bf66b167dea170c0c5fae8285aa40af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780971"
---
# <a name="source-control-integration-essentials"></a>Nozioni fondamentali sull'integrazione del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta due tipi di integrazione del controllo codice sorgente: un controllo del codice sorgente del plug-in che fornisce funzionalità di base e viene creato usando l'API dei plug-in del controllo origine (precedentemente noto come API MSSCCI) e una soluzione di integrazione del controllo codice sorgente basato sul pacchetto VSPackage che fornisce la funzionalità più affidabili.  
  
## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente  
 Un plug-in controllo di origine viene scritto come DLL che implementa l'API dei plug-in del controllo origine. Funzionalità di integrazione di controllo di origine e di registrazione viene fornita tramite l'API. Questo approccio è più facile da implementare rispetto a un pacchetto VSPackage di controllo di origine e Usa il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaccia utente (UI) per la maggior parte delle operazioni del controllo codice sorgente.  
  
 Per implementare un controllo del codice sorgente del plug-in usando l'API dei plug-in del controllo origine, seguire questa procedura:  
  
1. Creare una DLL che implementa le funzioni specificate nei [Plug-in controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2. Registrare la DLL, rendendo le voci del Registro di sistema appropriato, come descritto in [procedura: installare un plug-in controllo sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Creare un helper dell'interfaccia utente e visualizzarlo quando richiesto dal pacchetto di scheda di controllo di origine (il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componente che gestisce la funzionalità di controllo sorgente tramite plug-in controllo codice sorgente).  
  
   Per altre informazioni, vedere [creazione di un plug-in controllo sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage di controllo codice sorgente  
 Implementazione di VSPackage un controllo del codice sorgente consente di sviluppare una sostituzione personalizzata per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] controllo dell'interfaccia utente del codice sorgente. Questo approccio offre controllo completo sull'integrazione del controllo codice sorgente, ma richiede fornire elementi dell'interfaccia utente e implementare le interfacce di controllo di origine che in caso contrario, viene fornite con l'approccio del plug-in.  
  
 Per implementare un pacchetto VSPackage di controllo di origine, è necessario:  
  
1. Creare e registrare il proprio controllo del codice sorgente VSPackage, come descritto in [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Sostituire il controllo del codice sorgente predefinite dell'interfaccia utente con l'interfaccia utente personalizzata. Visualizzare [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Specificare i glifi da utilizzare e gestire **Esplora soluzioni** eventi glifo. Visualizzare [controllo Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Gestire gli eventi di Query modificare e salvare Query, come illustrato nella [salvataggio delle Query Edit Query](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Per altre informazioni, vedere [creazione di un VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di un controllo del codice sorgente del plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

