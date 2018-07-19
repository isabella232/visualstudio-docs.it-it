---
title: 'Procedura: associare estensioni di codice ai documenti gestito'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6e39f27caf9d321bb83666d72114a9675091f03
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257043"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: associare estensioni di codice ai documenti gestito
  È possibile collegare un assembly di personalizzazione in un documento esistente di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel. Il documento o la cartella di lavoro può essere in qualsiasi formato di file che è supportato per i progetti di Microsoft Office e gli strumenti di sviluppo in Visual Studio. Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Per collegare una personalizzazione a un documento di Word o Excel, usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo di <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Poiché il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe è progettata per essere eseguito su un computer in cui è installato Microsoft Office, è possibile usare questo metodo nelle soluzioni che non sono direttamente correlate allo sviluppo di Microsoft Office (ad esempio, un'applicazione Windows Forms o console).  
  
> [!NOTE]  
>  La personalizzazione non verrà caricato se il codice prevede che i controlli che non hanno il documento specificato.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come ricerca per categorie: collegare o scollegare un assembly VSTO da un documento di Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per associare estensioni di codice gestito a un documento  
  
1.  In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento per la *ServerDocument* e  *VisualStudio* assembly.  
  
2.  Aggiungere il codice seguente **importazioni** oppure **usando** istruzioni all'inizio del file di codice.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> (metodo).  
  
     Il codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> rapporto di overload. Questo overload accetta il percorso completo del documento e una <xref:System.Uri> che specifica il percorso del manifesto della distribuzione per la personalizzazione si desidera collegare al documento. Questo esempio si presuppone che un documento di Word denominato **WordDocument1.docx** sul desktop, e che il manifesto di distribuzione si trova in una cartella denominata **Publish** che è anche sul desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera collegare la personalizzazione. Il computer deve disporre di Visual Studio 2010 Tools per Office Runtime installato.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  