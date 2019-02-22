---
title: 'Procedura: Rimuovere estensioni di codice gestito dai documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d4b1e315d335215c990329380739f5fbf34997d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625855"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procedura: Rimuovere estensioni di codice gestito dai documenti
  È possibile rimuovere l'assembly di personalizzazione a livello di codice da un documento o cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel. Gli utenti possono quindi aprire i documenti e visualizzare il contenuto, ma non verrà visualizzata un'interfaccia utente personalizzata (UI) è aggiungere ai documenti e non verrà eseguito il codice.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile rimuovere l'assembly di personalizzazione utilizzando uno dei `RemoveCustomization` metodi forniti dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Il metodo da adottare dipende dal fatto che si desidera rimuovere la personalizzazione in fase di esecuzione (vale a dire, l'esecuzione di codice nella personalizzazione quando la parola documento o cartella di lavoro di Excel è aperto), o se si desidera rimuovere la personalizzazione da un documento chiuso o un documento che i s in un server che non è installato Microsoft Office.

 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [procedura: Collegare o scollegare un Assembly VSTO da un documento di Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

## <a name="to-remove-the-customization-assembly-at-runtime"></a>Per rimuovere l'assembly di personalizzazione in fase di esecuzione

1.  Nel codice della personalizzazione, chiamare il <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> metodo (per Word) o il <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (metodo) (per Excel). Questo metodo deve essere chiamato solo dopo la personalizzazione non è più necessario.

     In cui viene chiamato questo metodo nel codice dipende dal modo in cui viene utilizzata la personalizzazione. Ad esempio, se i clienti di usano le funzionalità della personalizzazione fino a quando non sono pronti per inviare il documento agli altri client che devono solo eseguire il documento stesso (non la personalizzazione), è possibile fornire un'interfaccia utente che chiama `RemoveCustomization` quando fa clic, il cliente. In alternativa, se la personalizzazione consente di popolare il documento con i dati quando si apre la prima volta, ma la personalizzazione non fornisce altre funzionalità che sono accessibili direttamente dai clienti, è possibile chiamare RemoveCustomization appena la personalizzazione al termine dell'inizializzazione del documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Per rimuovere l'assembly di personalizzazione da un documento chiuso o un documento in un server

1.  In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento per la *ServerDocument* assembly.

2.  Aggiungere il codice seguente **importazioni** oppure **usando** istruzione all'inizio del file di codice.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodo di <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe e specificare il percorso del documento della soluzione per il parametro.

     Esempio di codice seguente si presuppone che si stia rimuovendo la personalizzazione da un documento denominato *WordDocument1.docx* sul desktop.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera rimuovere la personalizzazione. Il computer deve disporre di Visual Studio 2010 Tools per Office runtime installato.

## <a name="see-also"></a>Vedere anche
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: Associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
