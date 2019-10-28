---
title: 'Procedura: associazione di estensioni di codice gestito a documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985970"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: associazione di estensioni di codice gestito a documenti
  È possibile aggiungere un assembly di personalizzazione a un documento Microsoft Office Word esistente o Microsoft Office cartella di lavoro di Excel. Il documento o la cartella di lavoro può essere in qualsiasi formato di file supportato dai progetti Microsoft Office e dagli strumenti di sviluppo in Visual Studio. Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per alleghi una personalizzazione a un documento di Word o di Excel, usare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>. Poiché la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> è progettata per essere eseguita in un computer in cui non è installato Microsoft Office, è possibile utilizzare questo metodo in soluzioni non direttamente correlate allo sviluppo di Microsoft Office (ad esempio una console o Windows Forms Application).

> [!NOTE]
> Il caricamento della personalizzazione non verrà eseguito se il codice prevede controlli che il documento specificato non dispone di.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per aggiungere estensioni di codice gestito a un documento

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento a *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* e  *Assembly Microsoft. VisualStudio. Tools. Applications. Runtime. dll* .

2. Aggiungere le istruzioni **Imports** o **using** seguenti all'inizio del file di codice.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.

     Nell'esempio di codice riportato di seguito viene utilizzato l'overload <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>. Questo overload accetta il percorso completo del documento e un <xref:System.Uri> che specifica il percorso del manifesto di distribuzione per la personalizzazione che si vuole alleghi al documento. In questo esempio si presuppone che un documento di Word denominato **WordDocument1. docx** si trovi sul desktop e che il manifesto di distribuzione si trovi in una cartella denominata **Publish** anch ' essa sul desktop.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera alleghi la personalizzazione. Nel computer deve essere installato Visual Studio 2010 Tools per Office Runtime.

## <a name="see-also"></a>Vedere anche
- [Gestire i documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: rimuovere estensioni di codice gestito da documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
