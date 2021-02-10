---
title: 'Procedura: rimuovere estensioni di codice gestito da documenti'
description: Rimuovere a livello di codice l'assembly di personalizzazione da un documento o una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Word o Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fea8a8f73155875f9a10e9d8138ee4b345d531d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942152"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procedura: rimuovere estensioni di codice gestito da documenti
  È possibile rimuovere a livello di codice l'assembly di personalizzazione da un documento o una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel. Gli utenti possono quindi aprire i documenti e visualizzare il contenuto, ma qualsiasi interfaccia utente personalizzata aggiunta ai documenti non verrà visualizzata e il codice non verrà eseguito.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile rimuovere l'assembly di personalizzazione utilizzando uno dei `RemoveCustomization` metodi forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Il metodo utilizzato varia a seconda che si desideri rimuovere la personalizzazione in fase di esecuzione, ovvero eseguendo codice nella personalizzazione mentre il documento di Word o la cartella di lavoro di Excel è aperta, oppure se si desidera rimuovere la personalizzazione da un documento chiuso o da un documento che si trova in un server in cui non è installato Microsoft Office.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Per rimuovere l'assembly di personalizzazione in fase di esecuzione

1. Nel codice di personalizzazione chiamare il <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> Metodo (per Word) o il <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> Metodo (per Excel). Questo metodo deve essere chiamato solo dopo che la personalizzazione non è più necessaria.

     La posizione in cui viene chiamato il metodo nel codice dipende dalla modalità di utilizzo della personalizzazione. Se, ad esempio, i clienti utilizzano le funzionalità della personalizzazione fino a quando non sono pronte per inviare il documento ad altri client che necessitano solo del documento stesso (non della personalizzazione), è possibile fornire un'interfaccia utente che chiama `RemoveCustomization` quando il cliente fa clic su di essa. In alternativa, se la personalizzazione compila il documento con i dati quando viene aperto per la prima volta, ma la personalizzazione non fornisce altre funzionalità accessibili direttamente dai clienti, è possibile chiamare RemoveCustomization non appena la personalizzazione completa l'inizializzazione del documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Per rimuovere l'assembly di personalizzazione da un documento chiuso o da un documento in un server

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Form, aggiungere un riferimento all'assembly di *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

2. Aggiungere la seguente istruzione **Imports** o **using** all'inizio del file di codice.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Chiamare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodo statico della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe e specificare il percorso del documento della soluzione per il parametro.

     Nell'esempio di codice seguente si presuppone che la personalizzazione venga rimossa da un documento denominato *WordDocument1.docx* sul desktop.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera rimuovere la personalizzazione. Nel computer deve essere installato Visual Studio 2010 Tools per Office Runtime.

## <a name="see-also"></a>Vedi anche
- [Gestire i documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: associazione di estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
