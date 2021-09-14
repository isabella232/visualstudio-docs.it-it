---
title: Protezione dei documenti nelle soluzioni a livello di documento
description: Informazioni su come usare le funzionalità di protezione di Microsoft Office Word e Microsoft Office Excel nei progetti a livello di documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cc11241057a32d24746eb9eabbc6a7b6526c9eaa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634116"
---
# <a name="document-protection-in-document-level-solutions"></a>Protezione dei documenti nelle soluzioni a livello di documento
  È possibile usare le funzionalità di protezione di Microsoft Office Word e Microsoft Office Excel nei progetti a livello di documento. Queste funzionalità bloccano gli utenti non autorizzati di apportare modifiche alle parti protette di un documento.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Usando Excel, è possibile attivare e disattivare la protezione mentre la cartella di lavoro è aperta nella finestra di progettazione. Con Word è possibile attivare la protezione solo all'esterno della finestra di progettazione. In fase di esecuzione è possibile abilitare o disabilitare la protezione a livello di codice sia per Word che per Excel.

 Quando la protezione dei documenti è abilitata in un documento  aperto nella finestra di progettazione, tutti  i controlli vengono rimossi dalla casella degli strumenti o resi non disponibili e non è possibile trascinare alcun elemento dalla finestra Origini dati al documento.

## <a name="serverdocument-and-protected-documents"></a>Documenti ServerDocument e protetti
 Se un documento è protetto, non è possibile accedere alla cache dei dati dall'esterno del documento. Non è possibile usare la classe per recuperare o modificare i dati memorizzati nella cache in un documento protetto o usare <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> altri metodi della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

## <a name="word-document-protection-in-the-designer"></a>Protezione dei documenti di Word nella finestra di progettazione
 Se si aggiunge la protezione a un documento o a un modello di Word mentre è aperto in Visual Studio, non è possibile iniziare ad applicazione della protezione nella finestra di progettazione. Il documento è in modalità progettazione mentre è aperto in Visual Studio e deve essere in modalità di esecuzione prima di poter avviare l'applicazione della protezione.

 Tuttavia, se si crea un progetto che usa un documento di Word esistente con la protezione abilitata, il documento viene protetto durante l'apertura nella finestra di progettazione. Non è possibile modificare le parti protette del documento, ma è comunque possibile scrivere codice nell'editor di codice per automatizzare il documento. Non è inoltre possibile compilare il progetto se la protezione è abilitata mentre il documento è aperto in Visual Studio.

 È possibile disattivare la protezione mentre il documento è aperto nella finestra di progettazione in modo da poter modificare il documento e compilare il progetto. Non è possibile disattivare la protezione per la copia nella finestra di progettazione durante il debug. Il documento aperto durante il debug è una copia separata da quella aperta nella finestra di progettazione (la copia di output viene archiviata nella directory *\bin* per Visual Basic e nella directory *\bin\debug* per C#).

 È possibile abilitare la protezione sulla copia del documento aperta nella finestra di progettazione chiudendo il progetto in Visual Studio, aprendo la copia del documento presente nella directory del progetto e attivando la protezione.

## <a name="enforce-word-document-protection-on-build"></a>Applicare la protezione dei documenti di Word alla compilazione
 Visual Studio viene avviata l'applicazione della protezione per i documenti e i modelli di Word durante il processo di compilazione, in modo che la protezione sia abilitata all'apertura del documento per il debug. Il documento è protetto con una password vuota.

 La protezione viene abilitata durante la compilazione in modo che se nell'evento del documento è presente codice che potrebbe causare eccezioni o modificare il comportamento dell'applicazione, il debug di questo codice può <xref:Microsoft.Office.Tools.Word.Document.Startup> essere eseguito correttamente. Se si abilita la protezione dopo l'apertura del documento, non è possibile eseguire il debug o il test del codice di inizializzazione.

## <a name="setting-the-password"></a>Impostazione della password
 Visual Studio automaticamente la protezione, ma non fornisce alcuna password per impostazione predefinita. Se si vuole che la protezione del documento abbia una password, è necessario aggiungerla prima di distribuire la soluzione. L'aggiunta di una password consente agli utenti autorizzati di rimuovere la protezione dal documento. senza una password, la protezione non può essere facilmente rimossa. Per informazioni dettagliate sull'impostazione di una password, vedere la Guida nell'applicazione Office specifica.

## <a name="see-also"></a>Vedi anche
- [Procedura: Proteggere documenti e parti di documenti a livello di codice](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office e procedure dettagliate per lo sviluppo di applicazioni](../vsto/office-development-samples-and-walkthroughs.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione della password nei Office documenti](../vsto/password-protection-on-office-documents.md)
- [Procedura: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
