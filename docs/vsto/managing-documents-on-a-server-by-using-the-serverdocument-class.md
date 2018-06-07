---
title: Gestire documenti in un server utilizzando la classe ServerDocument
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97eed0e4cec143e51195347bfb90d430d8e1eadb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572998"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gestire documenti in un server utilizzando la classe ServerDocument
  È possibile usare il `ServerDocument` classe il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per gestire diversi aspetti delle personalizzazioni a livello di documento, anche se Microsoft Office Word e Microsoft Office Excel non sono installati. È possibile eseguire le attività seguenti:  
  
-   Accedere e modificare i dati nella cache dei dati di un documento o una cartella di lavoro. Per altre informazioni, vedere [operare sui dati memorizzati nella cache nel documento](#CachedData).  
  
-   Gestire l'assembly di personalizzazione che viene associato a un documento. Per altre informazioni, vedere [gestire la personalizzazione del documento](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Comprendere la classe ServerDocument  
 Il `ServerDocument` classe è progettata per essere utilizzato nei computer che non è installato Office. Pertanto, in genere si utilizza questa classe nelle applicazioni che non si integrano con Office, ad esempio progetti di Console o Windows Form, anziché i progetti di Office. Usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe il *ServerDocument* assembly.  
  
 Il `ServerDocument` classe può essere utilizzata su cui operare delle personalizzazioni a livello di documento create mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Per ulteriori informazioni su Visual Studio 2010 Tools per Office Runtime e le estensioni di Office per .NET Framework, vedere [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Se si dispone di un'applicazione legacy che usa il `ServerDocument` classe il `Visual Studio Tools for Office` system (versione 3.0 Runtime), il `Visual Studio Tools for Office` system (versione 3.0 runtime) deve essere installato nei computer che eseguono l'applicazione. Il `Visual Studio 2010 Tools for Office runtime` non è possibile eseguire queste applicazioni.  
  
##  <a name="CachedData"></a> Utilizzare i dati memorizzati nella cache nel documento  
 Il `ServerDocument` classe fornisce membri che è possibile utilizzare per funzionare con la cache dei dati nei documenti personalizzati. Per ulteriori informazioni sui dati memorizzati nella cache, vedere [memorizzare dati nella Cache](../vsto/caching-data.md) e [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Nella tabella seguente sono elencati i membri che è possibile utilizzare per lavorare con i dati memorizzati nella cache.  
  
|Attività|Membro da usare|  
|----------|-------------------|  
|Per determinare se un documento dispone di una cache di dati.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Per accedere ai dati memorizzati nella cache in un documento.<br /><br /> Per altre informazioni, vedere [l'accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gestire la personalizzazione del documento  
 È possibile usare membri del `ServerDocument` classe per gestire l'assembly di personalizzazione che viene associato a un documento. Ad esempio, è possibile rimuovere a livello di codice la personalizzazione da un documento in modo che il documento non è più parte di una personalizzazione.  
  
 Nella tabella seguente sono elencati i membri che è possibile utilizzare per gestire l'assembly di personalizzazione.  
  
|Attività|Membro da usare|  
|----------|-------------------|  
|Per determinare se un documento fa parte di una personalizzazione a livello di documento.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Per associare a livello di codice una personalizzazione a un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [procedura: associare estensioni di codice ai documenti gestito](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodi.|  
|Per rimuovere a livello di codice una personalizzazione da un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [procedura: rimuovere il codice estensioni gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Per ottenere l'URL del manifesto di distribuzione che viene associato al documento.|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: associare estensioni di codice ai documenti gestito](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Dati nella cache](../vsto/caching-data.md)  
  