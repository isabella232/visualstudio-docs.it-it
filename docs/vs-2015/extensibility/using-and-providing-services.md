---
title: Uso e fornitura di servizi | Microsoft Docs
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
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: facf0bb9968e3ffbc9a68eb8eee906f300eb1859
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540848"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [sull'utilizzo e la fornitura di servizi](https://docs.microsoft.com/visualstudio/extensibility/using-and-providing-services).  
  
Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage offre un set specifico di interfacce per un altro VSPackage da utilizzare. Ad esempio, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servirla a qualsiasi pacchetto Carica. Questo servizio offre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usato per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
 I VSPackage possono offrire servizi di autonomamente usando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia...  
  
 Visual Studio offre servizi importanti, come il seguente:  
  
|Servizio IDE|Descrizione|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce la gestione dei servizi l'accesso all'IDE con funzionalità di base, i pacchetti VSPackage e nel Registro di sistema.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità legate all'interfaccia utente dell'IDE, ad esempio la possibilità di creare strumenti e finestre di documento e windowing di base.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce correlati alla soluzione funzionalità di base, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche del progetto.|  
  
## <a name="in-this-section"></a>In questa sezione  
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)  
 Visualizza gli elementi importanti di un servizio di Visual Studio.  
  
 [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md)  
 Viene illustrato come richiedere (utilizzare) un servizio.  
  
 [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md)  
 Viene spiegato come offrire un servizio.  
  
 [Procedura: Fornire un servizio asincrono di Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Viene spiegato come offrire un servizio asincrono.  
  
 [Procedura: Risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md)  
 Vengono illustrati i problemi comuni e vengono presentate le soluzioni ad essi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

