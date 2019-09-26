---
title: Protezione di documenti nelle soluzioni a livello di documento
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253813"
---
# <a name="document-protection-in-document-level-solutions"></a>Protezione di documenti nelle soluzioni a livello di documento
  È possibile utilizzare le funzionalità di protezione di Microsoft Office Word e Microsoft Office Excel nei progetti a livello di documento. Queste funzionalità impediscono a utenti non autorizzati di apportare modifiche alle parti protette di un documento.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Utilizzando Excel, è possibile attivare e disattivare la protezione mentre la cartella di lavoro è aperta nella finestra di progettazione. Con Word è possibile attivare la protezione solo all'esterno della finestra di progettazione. In fase di esecuzione, è possibile abilitare o disabilitare la protezione a livello di codice per Word ed Excel.

 Quando la protezione dei documenti è abilitata in un documento aperto nella finestra di progettazione, tutti i controlli vengono rimossi dalla **casella degli strumenti** o resi non disponibili e non è possibile trascinare elementi dalla finestra **origini dati** al documento.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument e documenti protetti
 Se un documento è protetto, non è possibile accedere alla cache dei dati dall'esterno del documento. Non è possibile utilizzare <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> la classe per recuperare o modificare i dati memorizzati nella cache in un documento protetto oppure utilizzare altri metodi <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> della classe.

## <a name="word-document-protection-in-the-designer"></a>Protezione dei documenti di Word nella finestra di progettazione
 Se si aggiunge la protezione a un documento o a un modello di Word mentre è aperto in Visual Studio, non è possibile avviare l'applicazione della protezione nella finestra di progettazione. Il documento è in modalità progettazione mentre è aperto in Visual Studio e deve essere in modalità di esecuzione prima di poter avviare l'applicazione della protezione.

 Tuttavia, se si crea un progetto che usa un documento di Word esistente in cui è abilitata la protezione, il documento viene protetto mentre è aperto nella finestra di progettazione. Non è possibile modificare le parti protette del documento, ma è comunque possibile scrivere codice nell'editor del codice per automatizzare il documento. Non è inoltre possibile compilare il progetto se la protezione è abilitata mentre il documento è aperto in Visual Studio.

 È possibile disattivare la protezione mentre il documento è aperto nella finestra di progettazione in modo che sia possibile modificare il documento e compilare il progetto. Non è possibile disattivare la protezione per la copia nella finestra di progettazione durante il debug; il documento che viene aperto durante il debug è una copia separata da quella aperta nella finestra di progettazione (la copia di output viene archiviata nella directory *\bin* per Visual Basic e la directory C# *\bin\Debug* per).

 È possibile abilitare la protezione per la copia del documento che viene aperta nella finestra di progettazione chiudendo il progetto in Visual Studio, aprendo la copia del documento che si trova nella directory del progetto e attivando la protezione.

## <a name="enforce-word-document-protection-on-build"></a>Applicare la protezione documenti di Word per la compilazione
 Visual Studio avvia l'applicazione della protezione per i documenti e i modelli di Word durante il processo di compilazione, in modo che la protezione sia abilitata quando il documento viene aperto per il debug. Il documento è protetto con una password vuota.

 La protezione viene abilitata durante la compilazione in modo che, se è <xref:Microsoft.Office.Tools.Word.Document.Startup> presente codice nell'evento del documento che potrebbe causare eccezioni o modificare il comportamento dell'applicazione, è possibile eseguire correttamente il debug di questo codice. Se si Abilita la protezione dopo l'apertura del documento, non è possibile eseguire il debug o il test del codice di inizializzazione.

## <a name="setting-the-password"></a>Impostazione della password
 Visual Studio Abilita automaticamente la protezione, ma non fornisce alcuna password per impostazione predefinita. Se si vuole che la protezione dei documenti disponga di una password, è necessario aggiungerla prima di distribuire la soluzione. L'aggiunta di una password consente di consentire agli utenti autorizzati di rimuovere la protezione dal documento; senza una password, non è possibile rimuovere facilmente la protezione. Per informazioni dettagliate sull'impostazione di una password, vedere la guida nell'applicazione di Office specifica.

## <a name="see-also"></a>Vedere anche
- [Procedura: Proteggere documenti e parti di documenti a livello di codice](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione delle password nei documenti di Office](../vsto/password-protection-on-office-documents.md)
- [Procedura: Consentire l'esecuzione del codice dietro i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
