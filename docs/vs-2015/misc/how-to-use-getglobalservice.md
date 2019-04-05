---
title: 'Procedura: Usare GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 0161b3e44b44567166a337d94101778074561e80
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58965737"
---
# <a name="how-to-use-getglobalservice"></a>Procedura: Usare GetGlobalService
In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività all'interno di un controllo. Per altre informazioni su questi e altri scenari, vedere [come: Risolvere i problemi di servizi](../extensibility/how-to-troubleshoot-services.md).  
  
 È possibile ottenere la maggior parte degli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] services chiamando il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (metodo).  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> si basa su un provider di servizi memorizzato nella cache che viene inizializzato al primo qualsiasi pacchetto VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package> viene individuato. È necessario garantire che questa condizione viene soddisfatta, altrimenti essere preparata per un servizio null.  
  
 Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona correttamente la maggior parte dei casi.  
  
-   Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene individuato prima il pacchetto VSPackage che fornisce che il servizio sia caricato.  
  
-   Se una finestra degli strumenti viene creata da un pacchetto VSPackage, il pacchetto VSPackage è collocato prima che venga creata la finestra degli strumenti.  
  
-   Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un pacchetto VSPackage, il pacchetto VSPackage è collocato prima che venga creato il contenitore del controllo.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di un contenitore di controllo o finestra degli strumenti  
  
-   Inserire questo codice nel costruttore, finestra degli strumenti o contenitore di controlli:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usato per scrivere nel log attività. Per un esempio, vedere [Procedura: Usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Risolvere i problemi di servizi](../extensibility/how-to-troubleshoot-services.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)