---
title: 'Procedura: utilizzare GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948182"
---
# <a name="how-to-use-getglobalservice"></a>Procedura: Usare GetGlobalService
In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non è in grado di conoscere il servizio desiderato. Ad esempio, potrebbe essere necessario scrivere nel log attività dall'interno di un controllo. Per ulteriori informazioni su questi e altri scenari, vedere [procedura: risoluzione dei problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md).  
  
 È possibile ottenere la maggior parte dei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Servizi chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo statico.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> si basa su un provider di servizi memorizzato nella cache che viene inizializzato alla prima esecuzione di un VSPackage derivato da <xref:Microsoft.VisualStudio.Shell.Package> . È necessario garantire che questa condizione sia soddisfatta o in caso contrario preparata per un servizio null.  
  
 Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona in modo corretto nella maggior parte dei casi.  
  
- Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene inserito prima del caricamento del pacchetto VSPackage che fornisce il servizio.  
  
- Se una finestra degli strumenti viene creata da un pacchetto VSPackage, il pacchetto VSPackage viene posto prima della creazione della finestra degli strumenti.  
  
- Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un pacchetto VSPackage, il pacchetto VSPackage viene inserito prima della creazione del contenitore del controllo.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di una finestra degli strumenti o di un contenitore di controlli  
  
- Inserire questo codice nel costruttore, nella finestra degli strumenti o nel contenitore di controlli:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usata per scrivere nel log attività. Per un esempio, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)