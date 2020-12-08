---
title: 'Procedura: associazione di estensioni di codice gestito a documenti'
description: Informazioni su come alleghi un assembly di personalizzazione a un documento Microsoft Office Word esistente o Microsoft Office cartella di lavoro di Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 1929daaa82dbfec6f58513bf94eefe01f9520601
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844388"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: associazione di estensioni di codice gestito a documenti
  È possibile aggiungere un assembly di personalizzazione a un documento Microsoft Office Word esistente o Microsoft Office cartella di lavoro di Excel. Il documento o la cartella di lavoro può essere in qualsiasi formato di file supportato dai progetti Microsoft Office e dagli strumenti di sviluppo in Visual Studio. Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per alleghi una personalizzazione a un documento di Word o di Excel, usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Poiché la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe è progettata per essere eseguita in un computer in cui non è installato Microsoft Office, è possibile utilizzare questo metodo in soluzioni non direttamente correlate allo sviluppo di Microsoft Office, ad esempio una console o Windows Forms Application.

> [!NOTE]
> Il caricamento della personalizzazione non verrà eseguito se il codice prevede controlli che il documento specificato non dispone di.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per aggiungere estensioni di codice gestito a un documento

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento agli assembly di *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* e *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* .

2. Aggiungere le istruzioni **Imports** o **using** seguenti all'inizio del file di codice.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Chiamare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo statico.

     Nell'esempio di codice riportato di seguito viene utilizzato l' <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Overload. Questo overload accetta il percorso completo del documento e un oggetto <xref:System.Uri> che specifica il percorso del manifesto di distribuzione per la personalizzazione che si vuole alleghi al documento. In questo esempio si presuppone che un documento di Word denominato **WordDocument1.docx** sia sul desktop e che il manifesto di distribuzione si trovi in una cartella denominata **Publish** che è anche sul desktop.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera alleghi la personalizzazione. Nel computer deve essere installato Visual Studio 2010 Tools per Office Runtime.

## <a name="see-also"></a>Vedi anche
- [Gestire i documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: rimuovere estensioni di codice gestito da documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
