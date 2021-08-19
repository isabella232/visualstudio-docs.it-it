---
title: 'Procedura: Rimuovere estensioni di codice gestito dai documenti'
description: Rimuovere a livello di codice l'assembly di personalizzazione da un documento o da una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Word o Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 233024b9e5dbd42908f8cd4b7a76cfd5a6901977
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155705"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procedura: Rimuovere estensioni di codice gestito dai documenti
  È possibile rimuovere a livello di codice l'assembly di personalizzazione da un documento o da una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel. Gli utenti possono quindi aprire i documenti e visualizzare il contenuto, ma qualsiasi interfaccia utente personalizzata aggiunta ai documenti non verrà visualizzata e il codice non verrà eseguito.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile rimuovere l'assembly di personalizzazione usando uno `RemoveCustomization` dei metodi forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Il metodo da usare varia a seconda che si voglia rimuovere la personalizzazione in fase di esecuzione( ovvero eseguendo il codice nella personalizzazione mentre il documento di Word o la cartella di lavoro di Excel è aperta) o se si vuole rimuovere la personalizzazione da un documento chiuso o da un documento che si trova in un server in cui non è installato Microsoft Office.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Per rimuovere l'assembly di personalizzazione in fase di esecuzione

1. Nel codice di personalizzazione chiamare il <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> metodo (per Word) o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> il metodo (per Excel). Questo metodo deve essere chiamato solo dopo che la personalizzazione non è più necessaria.

     La posizione in cui si chiama questo metodo nel codice dipende dal modo in cui viene usata la personalizzazione. Ad esempio, se i clienti usano le funzionalità della personalizzazione fino a quando non sono pronti a inviare il documento ad altri client che hanno solo bisogno del documento stesso (non della personalizzazione), è possibile fornire un'interfaccia utente che chiama quando il cliente fa clic su di `RemoveCustomization` esso. In alternativa, se la personalizzazione popola il documento con i dati alla prima apertura, ma la personalizzazione non fornisce altre funzionalità accessibili direttamente dai clienti, è possibile chiamare RemoveCustomization non appena la personalizzazione completa l'inizializzazione del documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Per rimuovere l'assembly di personalizzazione da un documento chiuso o da un documento in un server

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento all'assembly *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.*

2. Aggiungere **l'istruzione Imports** **o using** seguente all'inizio del file di codice.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. Chiamare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> statico della classe e specificare il percorso del documento della soluzione per il parametro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

     Nell'esempio di codice seguente si presuppone che la personalizzazione sia stata rimosso da un documento *WordDocument1.docx* sul desktop.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si vuole rimuovere la personalizzazione. Nel computer deve essere installato Visual Studio 2010 Tools for Office.

## <a name="see-also"></a>Vedi anche
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: Collegare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
