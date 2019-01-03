---
title: Protezione dei documenti nelle soluzioni a livello di documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6894aa05adf55945383cb3c2e28b8c5fdebdc16
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908853"
---
# <a name="document-protection-in-document-level-solutions"></a>Protezione dei documenti nelle soluzioni a livello di documento
  È possibile usare le funzionalità di protezione di Microsoft Office Word e Microsoft Office Excel nei progetti a livello di documento. Queste funzionalità impediscono agli utenti non autorizzati di apportare modifiche alle parti protette del documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Tramite Excel, è possibile attivare la protezione e disattivare mentre la cartella di lavoro è aperto nella finestra di progettazione. Utilizzo di Word, è possibile attivare la protezione solo all'esterno della finestra di progettazione. In fase di esecuzione, è possibile abilitare o disabilitare la protezione a livello di codice per Word ed Excel.  
  
 Quando è abilitata la protezione del documento in un documento aperto nella finestra di progettazione, tutti i controlli vengono rimossi dal **casella degli strumenti** o non sono disponibili, e non è possibile trascinare qualsiasi elemento dalle **Zdroje dat** finestra del documento.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument e documenti protetti  
 Se un documento è protetto, la cache dei dati non è accessibile all'esterno del documento. Non è possibile usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per recuperare o modificare i dati memorizzati nella cache in un documento protetto o usare altri metodi del <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> classe.  
  
## <a name="word-document-protection-in-the-designer"></a>Protezione di documenti di Word nella finestra di progettazione  
 Se si aggiunge protezione a un documento di Word o modello mentre è aperto in Visual Studio, è possibile avviare l'applicazione di protezione nella finestra di progettazione. Il documento è in modalità di progettazione mentre è aperto in Visual Studio e deve essere in esecuzione in modalità prima di poter avviare l'applicazione di protezione.  
  
 Tuttavia, se si crea un progetto che usa un documento Word esistente che è abilitata la protezione, il documento è protetto mentre era aperta nella finestra di progettazione. Non è possibile modificare le parti del documento protette, ma è comunque possibile scrivere codice nell'Editor di codice per automatizzare il documento. Inoltre, non è possibile compilare il progetto se la protezione è attivata mentre il documento è aperto in Visual Studio.  
  
 È possibile disattivare la protezione quando il documento è aperto nella finestra di progettazione in modo che è possibile modificare il documento e compilare il progetto. È possibile disabilitare la protezione per la copia nella finestra di progettazione durante il debug; il documento che viene aperto durante il debug è una copia distinta da quella aperta nella finestra di progettazione (la copia di output viene archiviata nel *\bin* directory per Visual Basic e il *\bin\Debug.* directory per C# ).  
  
 È possibile abilitare la protezione nella copia del documento che viene aperto nella finestra di progettazione, chiudere il progetto in Visual Studio, aprire la copia del documento è nella directory del progetto e attivare la protezione.  
  
## <a name="enforce-word-document-protection-on-build"></a>Applicare la protezione di documenti di Word in fase di compilazione  
 Visual Studio avvia l'applicazione di protezione per i documenti di Word e i modelli durante il processo di compilazione in modo che la protezione viene abilitata all'apertura del documento per il debug. Il documento è protetto con password vuota.  
  
 La protezione è abilitata durante la compilazione in modo che se il codice nel documento <xref:Microsoft.Office.Tools.Word.Document.Startup> evento che potrebbe generare eccezioni o modificare il comportamento dell'applicazione, questo codice può essere sottoposto a debug in modo corretto. Se si abilita la protezione dopo l'apertura del documento, il codice di inizializzazione non è possibile eseguire il debug o testato.  
  
## <a name="setting-the-password"></a>Impostazione della password  
 Visual Studio automaticamente abilita la protezione, ma non fornisce alcuna password per impostazione predefinita. Se si desidera che la protezione del documento di una password, è necessario aggiungere prima di distribuire la soluzione. Aggiunta di una password consente agli utenti autorizzati a rimuovere la protezione dal documento. senza una password, la protezione non è possibile rimuovere facilmente. Per informazioni dettagliate sull'impostazione di una password, vedere la Guida nell'applicazione di Office specifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: A livello di programmazione per proteggere documenti e parti di documenti](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information rights management e panoramica sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Password di protezione nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: Consentire l'esecuzione dietro i documenti con autorizzazioni limitate codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
