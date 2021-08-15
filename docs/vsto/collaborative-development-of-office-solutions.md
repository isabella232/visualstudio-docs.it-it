---
title: Sviluppo collaborativo di Office soluzioni
description: Informazioni su come più sviluppatori possono lavorare a un progetto Office nello stesso modo in cui collaborano ad altri Visual Studio progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cbe0c1544cb2d99b8958385affe1d972d5dc71c5f7a8192adcd63257f1cacd71
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268430"
---
# <a name="collaborative-development-of-office-solutions"></a>Sviluppo collaborativo di Office soluzioni
  Più sviluppatori possono lavorare a un Office progetto nello stesso modo in cui collaborano ad altri Visual Studio progetti. Visual Studio individua correttamente l Microsoft Office installazione in ogni computer, anche se Office installato in percorsi diversi. Esistono tuttavia alcune considerazioni importanti da tenere presenti.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Le proprietà di debug non sono condivise
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. i progetti Visual Basic e Visual C# archiviano le proprietà di debug in un file specifico dell'utente *(NomeProgetto*.vbproj.user o *NomeProgetto*.csproj.user) e questo file non è in controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.

 Se il progetto si trova in una condivisione di rete anziché nel controllo del codice sorgente, è necessario eseguire alcuni passaggi aggiuntivi per consentire agli sviluppatori che collaborano di aprire la soluzione e testare l'assembly.

## <a name="source-control-requires-checking-out-all-files"></a>Il controllo del codice sorgente richiede l'estrazione di tutti i file
 Se si usa il controllo del codice sorgente per i progetti, è necessario estrarre tutti i file in un file di codice in **Esplora soluzioni** (ad esempio i file di codice *ThisDocument*, *ThisWorkbook* o *ThisAddIn)* ogni volta che si modifica il file di codice, anche i file nascosti per impostazione predefinita. Se si estrae solo il file di codice di primo livello, le modifiche potrebbero essere perse.

 Dopo aver apportato le modifiche, archiviare nuovamente tutti i file. Per altre informazioni sui file di codice nascosti nei progetti, vedere [Office progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="security-for-informal-collaboration-on-a-network"></a>Sicurezza per la collaborazione informale in una rete
 Per tutte le soluzioni a livello di documento presenti in un percorso di rete, ad esempio NomeServerNome Condivisione , il percorso completo deve essere aggiunto all'elenco di cartelle attendibili nell'applicazione Microsoft Office in \\ \\  \\ uso. Selezionare l'opzione per includere le sottodirectory nella cartella principale o aggiungere in modo specifico cartelle di debug e compilazione all'elenco di cartelle attendibili. Per altre informazioni su come eseguire questa operazione, vedere Concedere [l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).

 I certificati temporanei generati automaticamente in fase di compilazione non sono protetti da password. I certificati contengono il nome di accesso dello sviluppatore e altre informazioni personali. Se si distribuiscono personalizzazioni firmate da certificati temporanei, altri utenti potrebbero essere in grado di accedere a queste informazioni.

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicurezza](../vsto/securing-office-solutions.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Creare Office soluzioni](../vsto/building-office-solutions.md)
