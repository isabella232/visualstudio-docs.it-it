---
title: Sviluppo collaborativo di soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62949487"
---
# <a name="collaborative-development-of-office-solutions"></a>Sviluppo collaborativo di soluzioni Office
  Più sviluppatori possono lavorare a un progetto di Office nello stesso modo in cui collaborano con altri progetti di Visual Studio. Visual Studio individua correttamente l'installazione di Microsoft Office in ogni computer, anche se Office è installato in posizioni diverse. Tuttavia, esistono alcune importanti considerazioni da tenere presenti.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Le proprietà di debug non sono condivise
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. I progetti Visual Basic e Visual C# archiviano le proprietà di debug in un file specifico dell'utente (*NomeProgetto*. vbproj. User o *NomeProgetto*. csproj. User) e questo file non è sotto il controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.

 Se il progetto è ospitato in una condivisione di rete anziché nel controllo del codice sorgente, è necessario eseguire alcuni passaggi aggiuntivi per consentire agli sviluppatori che collaborano di aprire la soluzione e testare l'assembly.

## <a name="source-control-requires-checking-out-all-files"></a>Il controllo del codice sorgente richiede l'estrazione di tutti i file
 Se si usa il controllo del codice sorgente per i progetti, è necessario estrarre tutti i file in un file di codice in **Esplora soluzioni** , ad esempio i file di codice *ThisDocument*, *ThisWorkbook*o *ThisAddIn* , ogni volta che si modifica il file di codice, anche i file che sono nascosti per impostazione predefinita. Se si estrae solo il file di codice di primo livello, le modifiche potrebbero andare perse.

 Dopo aver apportato le modifiche, controllare tutti i file di nuovo in. Per altre informazioni sui file di codice nascosti nei progetti, vedere [progetti di Office nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Sicurezza per la collaborazione informale in una rete
 Per tutte le soluzioni a livello di documento in un percorso di rete (ad esempio \\ \\ *nomeserver* \\ *ShareName*), il percorso completo deve essere aggiunto all'elenco di cartelle attendibili nell'applicazione Microsoft Office che si sta utilizzando. Selezionare l'opzione per includere le sottodirectory nella cartella principale o aggiungere in modo specifico le cartelle debug e Build all'elenco di cartelle attendibili. Per ulteriori informazioni su come eseguire questa operazione, vedere [Grant trust to Documents](../vsto/granting-trust-to-documents.md).

 I certificati temporanei generati automaticamente in fase di compilazione non sono protetti da password. I certificati contengono il nome di accesso dello sviluppatore e altre informazioni personali. Se si distribuiscono personalizzazioni firmate da certificati temporanei, altri utenti potrebbero essere in grado di accedere a queste informazioni.

## <a name="see-also"></a>Vedere anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)
