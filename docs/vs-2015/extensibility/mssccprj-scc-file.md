---
title: Mssccprj. File SCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194211"
---
# <a name="mssccprjscc-file"></a>File MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando una soluzione o un progetto di Visual Studio viene inserito nel controllo del codice sorgente usando l'IDE, l'IDE riceve due informazioni chiave dal plug-in del controllo del codice sorgente sotto forma di stringhe. Queste stringhe, "AuxPath" e "ProjName", sono opache per l'IDE, ma vengono usate dal plug-in per individuare la soluzione o il progetto nel controllo della versione. In genere, l'IDE ottiene queste stringhe la prima volta chiamando il [SccGetProjPath](../extensibility/sccgetprojpath-function.md)e quindi le salva nel file di soluzione o di progetto per le chiamate future al [SccOpenProject](../extensibility/sccopenproject-function.md). Quando incorporati nei file di soluzione e di progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente esegue il branching, il fork o copia i file della soluzione e del progetto presenti nel controllo della versione. Per assicurarsi che la soluzione e i file di progetto puntino al percorso corretto nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe sono pensate per essere opache, potrebbe non essere sempre chiaro come devono essere aggiornate.  
  
 Il plug-in del controllo del codice sorgente può evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato MSSCCPRJ. File SCC. Si tratta di un file locale, sul lato client, di proprietà e gestito dal plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma viene generato dal plug-in per ogni directory che contiene i file inclusi nel controllo del codice sorgente. Per determinare quali file sono i file di soluzione e di progetto di Visual Studio, un plug-in del controllo del codice sorgente può confrontare le estensioni di file con un elenco standard o fornito dall'utente. Quando l'IDE rileva che un plug-in supporta MSSCCPRJ. Il file SCC smette di incorporare le stringhe "AuxPath" e "ProjName" in file di soluzione e di progetto e legge tali stringhe da MSSCCPRJ. In alternativa, il file SCC.  
  
 Plug-in del controllo del codice sorgente che supporta MSSCCPRJ. Il file SCC deve rispettare le seguenti linee guida:  
  
- Può essere presente un solo MSSCCPRJ. File SCC per ogni directory.  
  
- MSSCCPRJ. Il file SCC può contenere "AuxPath" e "ProjName" per più file sottoposti al controllo del codice sorgente all'interno di una determinata directory.  
  
- La stringa "AuxPath" non deve contenere le virgolette al suo interno. È consentito racchiuderlo tra virgolette come delimitatori (ad esempio, è possibile usare una coppia di virgolette doppie per indicare una stringa vuota). L'IDE esegue lo striping di tutte le virgolette dalla stringa "AuxPath" quando viene letta dal MSSCCPRJ. File SCC.  
  
- Stringa "ProjName" in MSSCCPRJ. Il file SCC deve corrispondere esattamente alla stringa restituita dalla `SccGetProjPath` funzione. Se la stringa restituita dalla funzione contiene virgolette, la stringa in MSSCCPRJ. Il file SCC deve racchiuderlo tra virgolette e viceversa.  
  
- MSSCCPRJ. Il file SCC viene creato o aggiornato ogni volta che un file viene inserito nel controllo del codice sorgente.  
  
- Se un MSSCCPRJ. Il file SCC viene eliminato, un provider deve rigenerarlo alla successiva esecuzione di un'operazione di controllo del codice sorgente relativa a tale directory.  
  
- MSSCCPRJ. Il file SCC deve rispettare rigorosamente il formato definito.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Illustrazione del MSSCCPRJ. Formato file SCC  
 Di seguito è riportato un esempio di MSSCCPRJ. Formato di file SCC (i numeri di riga vengono forniti solo come guida e non devono essere inclusi nel corpo del file):  
  
 [Riga 1] `SCC = This is a Source Code Control file`  
  
 [Riga 2]  
  
 [Riga 3] `[TestApp.sln]`  
  
 [Riga 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Riga 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Riga 6]  
  
 [Riga 7] `[TestApp.csproj]`  
  
 [Riga 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Riga 9] `SCC_Project_Name = "$/TestApp"`  
  
 La prima riga indica lo scopo del file e funge da firma per tutti i file di questo tipo. Questa riga dovrebbe apparire esattamente come questa in tutti MSSCCPRJ. File SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Di seguito è riportata una sezione di impostazioni per ogni file, contrassegnato dal nome file tra parentesi quadre. Questa sezione è ripetuta per ogni file rilevato. Questa riga è un esempio di nome di file, ovvero `[TestApp.csproj]` . L'IDE prevede le due righe seguenti. Non definisce tuttavia lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name` .  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Nessun delimitatore finale a questa sezione. Il nome del file, nonché tutti i valori letterali visualizzati nel file, vengono definiti nel file di intestazione SCC. h. Per ulteriori informazioni, vedere [stringhe utilizzate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
