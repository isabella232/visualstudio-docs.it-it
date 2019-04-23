---
title: MSSCCPRJ. File SCC | Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117720"
---
# <a name="mssccprjscc-file"></a>File MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando una soluzione di Visual Studio o un progetto viene inserito nel controllo del codice sorgente usare l'IDE, l'IDE riceve due tipi principali di informazioni dal controllo del codice sorgente del plug-in forma di stringhe. Queste stringhe "AuxPath" e "ProjName", sono opache per l'IDE, ma vengono utilizzati per il plug-in per individuare la soluzione o progetto in controllo della versione. L'IDE in genere Ottiene queste stringhe la prima volta chiamando il [SccGetProjPath](../extensibility/sccgetprojpath-function.md), e quindi li salva nel file di soluzione o il progetto per le chiamate successive al [SccOpenProject](../extensibility/sccopenproject-function.md). Se si incorpora nei file di soluzione e progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente di rami, fork, o copia i file di soluzione e progetto in controllo della versione. Per assicurarsi che i file di soluzione e progetto puntino alla posizione corretta nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe devono essere opaca, potrebbe non sempre essere chiaro come devono essere aggiornati.  
  
 Il plug-in del controllo del codice sorgente è possibile evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato il MSSCCPRJ. File di controllo del codice sorgente. È un file locale, sul lato client, che è di proprietà e gestito dal plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma viene generato il plug-in per tutte le directory che contiene i file di controllo del codice sorgente. Per determinare quali file sono file della soluzione e progetto di Visual Studio, un controllo del codice sorgente del plug-in grado di confrontare le estensioni di file rispetto a un elenco standard o fornita dall'utente. Una volta l'IDE rileva che un plug-in supporta il MSSCCPRJ. File di controllo del codice sorgente, cessa di incorporare "AuxPath" e "ProjName" stringhe nella soluzione e i file di progetto che legge tali stringhe dal MSSCCPRJ. Controllo del codice sorgente del file invece.  
  
 Un controllo del codice sorgente del plug-in che supporta il MSSCCPRJ. File SCC deve rispettare le linee guida seguenti:  
  
- Può essere presente solo uno MSSCCPRJ. File di controllo del codice sorgente per ogni directory.  
  
- Un MSSCCPRJ. File SCC può contenere il "AuxPath" e "ProjName" per più file sottoposti al controllo del codice sorgente all'interno di una determinata directory.  
  
- La stringa "AuxPath" non deve avere le offerte in essa contenuti. È consentito avere virgolette intorno a esso come delimitatori (ad esempio, una coppia di virgolette doppie possa essere consente di indicare una stringa vuota). L'IDE rimuoverà tutte le offerte dalla stringa "AuxPath" quando viene letta dal MSSCCPRJ. File di controllo del codice sorgente.  
  
- La stringa "Nomeprogetto" nel MSSCCPRJ. File SCC deve corrispondere esattamente alla stringa restituita dal `SccGetProjPath` (funzione). Se la stringa restituita dalla funzione contiene virgolette, la stringa nel MSSCCPRJ. File SCC deve includere le virgolette intorno a esso e viceversa.  
  
- Un MSSCCPRJ. File SCC viene creato o aggiornato ogni volta che un file viene inserito nel controllo del codice sorgente.  
  
- Se un MSSCCPRJ. File SCC viene eliminato, un provider deve generarla di nuovo la volta successiva che esegue un'operazione di controllo codice sorgente relativi a tale directory.  
  
- Un MSSCCPRJ. File SCC deve seguire rigorosamente il formato definito.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Un'illustrazione del MSSCCPRJ. Formato di File di controllo del codice sorgente  
 Seguito è riportato un esempio del MSSCCPRJ. Formato di file di controllo del codice sorgente (i numeri di riga vengono forniti solo come guida e non devono essere incluse nel corpo del file):  
  
 [Line 1] `SCC = This is a Source Code Control file`  
  
 [Line 2]  
  
 [Line 3] `[TestApp.sln]`  
  
 [Line 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Line 6]  
  
 [Line 7] `[TestApp.csproj]`  
  
 [Line 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 9] `SCC_Project_Name = "$/TestApp"`  
  
 La prima riga indica lo scopo del file e funge da firma per tutti i file di questo tipo. Questa riga dovrebbe essere esattamente come in tutti i MSSCCPRJ. File SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Ciò che segue è una sezione di impostazioni per ogni file è contrassegnato dal nome del file racchiusa tra parentesi quadre. In questa sezione viene ripetuta per ogni file rilevati. Questa riga è riportato un esempio di un nome di file, vale a dire, `[TestApp.csproj]`. L'IDE prevede le due righe seguenti. Non, tuttavia, definisce lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Non è disponibile alcun delimitatore finale a questa sezione. Il nome del file, nonché tutti i valori letterali presenti nel file sono definiti nel file di intestazione scc.h. Per altre informazioni, vedere [utilizzate stringhe come chiavi per la ricerca di un plug-in controllo sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
