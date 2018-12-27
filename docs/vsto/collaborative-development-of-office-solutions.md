---
title: Sviluppo collaborativo di soluzioni Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b4d22c92bd180eb27f8ebb50e65b24d17a92e47
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441548"
---
# <a name="collaborative-development-of-office-solutions"></a>Sviluppo collaborativo di soluzioni Office
  Più sviluppatori possono lavorare in un progetto di Office nello stesso modo in cui collaborano in altri progetti di Visual Studio. Visual Studio individua correttamente l'installazione di Microsoft Office su ogni computer, anche se è installato Office in posizioni diverse. Tuttavia, esistono alcune importanti considerazioni da tenere presenti.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Eseguire il debug delle proprietà non sono condivise  
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. Visual Basic e oggetto visivo C# progetti archiviano le proprietà di debug in un file specifico dell'utente (*NomeProgetto*. vbproj o *ProjectName*. csproj), e questo file non incluso nel controllo del codice sorgente . Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.  
  
 Se il progetto si trova in una condivisione di rete anziché nel controllo del codice sorgente, è necessario effettuare alcuni passaggi aggiuntivi per consentire agli sviluppatori di aprire la soluzione e assembly di test.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Controllo del codice sorgente è necessario estrarre tutti i file  
 Se si usa il codice sorgente per i progetti, è necessario estrarre tutti i file in un file di codice nel **Esplora soluzioni** (ad esempio le *ThisDocument*, *ThisWorkbook*, o *ThisAddIn* i file di codice) ogni volta che si modifica il file di codice, inclusi i file sono nascoste per impostazione predefinita. Se si estrae solo il file di codice di primo livello, le modifiche potrebbero andare perse.  
  
 Dopo aver apportato le modifiche apportate, controllare che tutti i file di nuovo. Per altre informazioni sui file di codice nascoste nei progetti, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Sicurezza per la collaborazione in una rete informale  
 Per tutte le soluzioni a livello di documento in un percorso di rete (ad esempio \\ \\ *Servername*\\*nomecondivisione*), il percorso completo deve essere aggiunto a elenco delle cartelle attendibili nell'applicazione Microsoft Office che si sta lavorando. Selezionare l'opzione per includere le sottodirectory nella cartella principale, o, in particolare, aggiungere debug e compilare cartelle all'elenco delle cartelle attendibili. Per altre informazioni su come eseguire questa operazione, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).  
  
 I certificati temporanei che vengono generati automaticamente in fase di compilazione non sono protetti da password. I certificati contengono il nome di accesso per gli sviluppatori e gli altri dati personali. Se si distribuiscono le personalizzazioni firmate da certificati temporanei, altre potrebbero essere in grado di accedere a queste informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Creazione di soluzioni Office](../vsto/building-office-solutions.md)  
  
  