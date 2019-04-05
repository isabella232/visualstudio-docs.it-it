---
title: Uso e fornitura di servizi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964068"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage offre un set specifico di interfacce per un altro VSPackage da utilizzare. Ad esempio, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servirla a qualsiasi pacchetto Carica. Questo servizio offre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usato per scrivere nel log attività. Per altre informazioni, vedere [Procedura: Usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
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
  
 [Procedura: Risolvere i problemi di servizi](../extensibility/how-to-troubleshoot-services.md)  
 Vengono illustrati i problemi comuni e vengono presentate le soluzioni ad essi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
