---
title: DI MSSCCPRJ. File SCC Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702474"
---
# <a name="mssccprjscc-file"></a>DI MSSCCPRJ. File SCC
Quando si inserisce una soluzione di Visual Studio o un progetto nel controllo del codice sorgente utilizzando l'IDE, l'IDE riceve due informazioni chiave. Le informazioni provengono dal plug-in del controllo del codice sorgente sotto forma di stringhe. Queste stringhe, "AuxPath" e "ProjName", sono opache per l'IDE, ma vengono utilizzate dal plug-in per individuare la soluzione o il progetto nel controllo della versione. L'IDE ottiene in genere queste stringhe la prima volta chiamando [SccGetProjPath](../extensibility/sccgetprojpath-function.md)e quindi le salva nel file di soluzione o di progetto per le chiamate future a [SccOpenProject](../extensibility/sccopenproject-function.md). Quando incorporato nei file di soluzione e di progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente dicquia, fork o copia i file di soluzione e di progetto che si trovano nel controllo della versione. Per assicurarsi che i file di soluzione e di progetto puntino alla posizione corretta nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe sono destinate ad essere opache, potrebbe non essere sempre chiaro come dovrebbero essere aggiornate.

 Il plug-in del controllo del codice sorgente può evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato file *MSSCCPRJ.SCC.* Si tratta di un file locale sul lato client che è di proprietà e gestito dal plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma viene generato dal plug-in per ogni directory che contiene file inclusi nel controllo del codice sorgente. Per determinare quali file sono file di soluzione e di progetto di Visual Studio, un plug-in del controllo del codice sorgente può confrontare le estensioni di file con un elenco standard o fornito dall'utente. Una volta che l'IDE rileva che un plug-in supporta il file *MSSCCPRJ.SCC,* cessa di incorporare le stringhe "AuxPath" e "ProjName" nei file di soluzione e di progetto e legge invece tali stringhe dal file *MSSCCPRJ.SCC.*

 Un plug-in del controllo del codice sorgente che supporta il file *MSSCCPRJ.SCC* deve rispettare le linee guida seguenti:

- Può essere presente un solo file *MSSCCPRJ.SCC* per directory.

- Un file *MSSCCPRJ.SCC* può contenere "AuxPath" e "ProjName" per più file che si trovano nel controllo del codice sorgente all'interno di una determinata directory.

- La stringa "AuxPath" non deve avere virgolette al suo interno. È consentito avere virgolette intorno ad esso come delimitatori (ad esempio, una coppia di virgolette doppie può essere utilizzato per indicare una stringa vuota). L'IDE rimuoverà tutte le virgolette dalla stringa "AuxPath" quando viene letto dal file *MSSCCPRJ.SCC.*

- La stringa "ProjName" in *MSSCCPRJ. Il file SCC* deve corrispondere esattamente `SccGetProjPath` alla stringa restituita dalla funzione. Se la stringa restituita dalla funzione contiene virgolette, la stringa nel file *MSSCCPRJ.SCC* deve avere virgolette intorno ad essa e viceversa.

- Un file *MSSCCPRJ.SCC* viene creato o aggiornato ogni volta che un file viene inserito nel controllo del codice sorgente.

- Se un file *MSSCCPRJ.SCC* viene eliminato, un provider deve rigenerarlo alla successiva esecuzione di un'operazione di controllo del codice sorgente relativa a tale directory.

- Un file *MSSCCPRJ.SCC* deve seguire rigorosamente il formato definito.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Un'illustrazione di MSSCCPRJ. Formato di file SCC
 Di seguito è riportato un esempio del formato di file *MSSCCPRJ.SCC* (i numeri di riga vengono forniti solo come guida e non devono essere inclusi nel corpo del file):

- [Linea 1]`SCC = This is a Source Code Control file`

- [Linea 2]

- [Linea 3]`[TestApp.sln]`

- [Linea 4]`SCC_Aux_Path = "\\server\vss\"`

- [Linea 5]`SCC_Project_Name = "$/TestApp"`

- [Linea 6]

- [Linea 7]`[TestApp.csproj]`

- [Linea 8]`SCC_Aux_Path = "\\server\vss\"`

- [Linea 9]`SCC_Project_Name = "$/TestApp"`

 La prima riga indica lo scopo del file e funge da firma per tutti i file di questo tipo. Questa riga dovrebbe apparire esattamente come questa in tutti i file *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 La sezione seguente descrive le impostazioni per ogni file, contrassegnate dal nome del file tra parentesi quadre. Questa sezione viene ripetuta per ogni file monitorato. Questa riga è un esempio di un `[TestApp.csproj]`nome di file, vale a dire, . L'IDE prevede le due righe seguenti. Non definisce tuttavia lo stile dei valori definiti. Le variabili `SCC_Aux_Path` `SCC_Project_Name`sono e .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Non esiste alcun delimitatore di fine per questa sezione. Il nome del file, nonché tutti i valori letterali visualizzati nel file, sono definiti nel file di intestazione scc.h. Per ulteriori informazioni, vedere [Stringhe utilizzate come chiavi per trovare un plug-in del controllo del codice sorgente.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Stringhe utilizzate come chiavi per trovare un plug-in del controllo del codice sorgenteStrings used as keys for finding a source control plug-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
