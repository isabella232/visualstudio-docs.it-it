---
title: 'Procedura: Collegare estensioni di codice gestito ai documenti'
description: Informazioni su come collegare un assembly di personalizzazione a un documento di Word Microsoft Office o a una cartella Microsoft Office Excel cartella di lavoro.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a20ba0be857c3ffecc0f7c35475931ae022ef833
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148259"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: Collegare estensioni di codice gestito ai documenti
  È possibile collegare un assembly di personalizzazione a un documento Microsoft Office Word o a Microsoft Office Excel cartella di lavoro. Il documento o la cartella di lavoro può essere in qualsiasi formato di file supportato dai progetti Microsoft Office e dagli strumenti di sviluppo in Visual Studio. Per altre informazioni, vedere [Architettura delle personalizzazioni a livello di documento.](../vsto/architecture-of-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per associare una personalizzazione a un documento di Word o Excel, usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe . Poiché la classe è progettata per essere eseguita in un computer in cui non è installato Microsoft Office, è possibile usare questo metodo in soluzioni non direttamente correlate allo sviluppo di Microsoft Office (ad esempio una console o un'applicazione <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Windows Forms).

> [!NOTE]
> La personalizzazione non verrà caricata se il codice prevede controlli che il documento specificato non ha.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per associare estensioni di codice gestito a un documento

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto  form Windows, aggiungere un riferimento agli assemblyMicrosoft.VisualStudio.Tools.Applications.ServerDocument.dlle *Microsoft.VisualStudio.Tools.Applications.Runtime.dll.*

2. Aggiungere le istruzioni **Imports** **o using** seguenti all'inizio del file di codice.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet4":::

3. Chiamare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> statico.

     Nell'esempio di codice seguente viene utilizzato <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> l'overload . Questo overload accetta il percorso completo del documento e un oggetto che specifica il percorso del manifesto di distribuzione per la personalizzazione da <xref:System.Uri> allegare al documento. Questo esempio presuppone che sul desktop sia presente un documento di Word denominato **WordDocument1.docx** e che il manifesto della distribuzione si trovi in una cartella denominata **Pubblica** che si trova anche sul desktop.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet3":::

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si vuole collegare la personalizzazione. Nel computer deve essere installato Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Vedi anche
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesti dell'applicazione e della distribuzione Office soluzioni](../vsto/application-and-deployment-manifests-in-office-solutions.md)
