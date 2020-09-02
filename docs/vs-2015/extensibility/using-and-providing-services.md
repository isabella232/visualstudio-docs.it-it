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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177433"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage offre un set specifico di interfacce per l'utilizzo da parte di un altro VSPackage. Ad esempio, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servizio a qualsiasi VSPackage caricato. Questo servizio fornisce l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usata per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).  
  
 I pacchetti VSPackage possono offrire servizi propri usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia.  
  
 Visual Studio offre importanti servizi, come i seguenti:  
  
|Servizio IDE|Descrizione|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce l'accesso ai servizi IDE che gestiscono le funzionalità di base, i pacchetti VSPackage e il registro di sistema.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce le funzionalità di base relative alla finestra e all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre dei documenti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità di base relative alla soluzione, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche del progetto.|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)  
 Vengono presentati gli elementi importanti di un servizio di Visual Studio.  
  
 [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md)  
 Viene illustrato come richiedere (utilizzare) un servizio.  
  
 [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md)  
 Viene illustrato come fornire un servizio.  
  
 [Procedura: Fornire un servizio asincrono di Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Viene illustrato come fornire un servizio asincrono.  
  
 [Procedura: Risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md)  
 Vengono illustrati i problemi comuni e vengono presentate soluzioni.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [SDK di Visual Studio](../extensibility/visual-studio-sdk.md)
