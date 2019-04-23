---
title: MSSCCPRJ. File SCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf9c2f914bbe0bed741a407faf1d0055a4b43a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043720"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. File SCC
Quando si inserisce una soluzione di Visual Studio o un progetto nel controllo del codice sorgente usare l'IDE, l'IDE riceve due tipi principali di informazioni. Le informazioni provengano da controllo del codice sorgente del plug-in forma di stringhe. Queste stringhe "AuxPath" e "ProjName", sono opache per l'IDE, ma vengono utilizzati per il plug-in per individuare la soluzione o progetto in controllo della versione. L'IDE in genere Ottiene queste stringhe la prima volta chiamando il [SccGetProjPath](../extensibility/sccgetprojpath-function.md), e quindi li salva nel file di soluzione o il progetto per le chiamate successive al [SccOpenProject](../extensibility/sccopenproject-function.md). Se si incorpora nei file di soluzione e progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente di rami, fork, o copia i file di soluzione e progetto in controllo della versione. Per assicurarsi che i file di soluzione e progetto puntino alla posizione corretta nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe devono essere opaca, potrebbe non sempre essere chiaro come devono essere aggiornati.

 Il plug-in del controllo del codice sorgente è possibile evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato il *Mssccprj. scc* file. È un file locale, sul lato client, che è di proprietà e gestito dal plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma viene generato il plug-in per tutte le directory che contiene i file di controllo del codice sorgente. Per determinare quali file sono file della soluzione e progetto di Visual Studio, un controllo del codice sorgente del plug-in grado di confrontare le estensioni di file rispetto a un elenco standard o fornita dall'utente. Una volta l'IDE rileva che un plug-in supporta il *Mssccprj. scc* cessa di incorporare le stringhe "AuxPath" e "ProjName" nel file di soluzione e progetto di file, e legge le stringhe dal *Mssccprj. scc*invece di file.

 Un controllo del codice sorgente del plug-in che supporta il *Mssccprj. scc* file deve rispettare le linee guida seguenti:

- Può essere presente solo uno *Mssccprj. scc* file per ogni directory.

- Un' *Mssccprj. scc* file può contenere il "AuxPath" e "ProjName" per più file sottoposti al controllo del codice sorgente all'interno di una determinata directory.

- La stringa "AuxPath" non deve avere le offerte in essa contenuti. È consentito avere virgolette intorno a esso come delimitatori (ad esempio, una coppia di virgolette doppie possa essere consente di indicare una stringa vuota). L'IDE rimuoverà tutte le offerte dalla stringa "AuxPath" quando viene letta dal *Mssccprj. scc* file.

- Stringa "Nomeprogetto" nel *MSSCCPRJ. File SCC* devono corrispondere esattamente alla stringa restituita dal `SccGetProjPath` (funzione). Se la stringa restituita dalla funzione contiene virgolette, la stringa nel *Mssccprj. scc* file deve includere le virgolette intorno a esso e viceversa.

- Un' *Mssccprj. scc* file viene creato o aggiornato ogni volta che un file viene inserito nel controllo del codice sorgente.

- Se un' *Mssccprj. scc* file viene eliminato, un provider deve generarla di nuovo la volta successiva che esegue un'operazione di controllo codice sorgente relativi a tale directory.

- Un' *Mssccprj. scc* file deve seguire rigorosamente il formato definito.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Un'illustrazione del MSSCCPRJ. Formato del file di controllo del codice sorgente
 Seguito è riportato un esempio del *Mssccprj. scc* formato di file (i numeri di riga vengono forniti solo come guida e non devono essere incluse nel corpo del file):

- [Line 1] `SCC = This is a Source Code Control file`

- [Line 2]

- [Line 3] `[TestApp.sln]`

- [Line 4] `SCC_Aux_Path = "\\server\vss\"`

- [Line 5] `SCC_Project_Name = "$/TestApp"`

- [Line 6]

- [Line 7] `[TestApp.csproj]`

- [Line 8] `SCC_Aux_Path = "\\server\vss\"`

- [Line 9] `SCC_Project_Name = "$/TestApp"`

 La prima riga indica lo scopo del file e funge da firma per tutti i file di questo tipo. Questa riga dovrebbe essere esattamente come in tutti i *Mssccprj. scc* file:

 `SCC = This is a Source Code Control file`

 La sezione seguente illustra in dettaglio le impostazioni per ogni file è contrassegnato dal nome del file racchiusa tra parentesi quadre. In questa sezione viene ripetuta per ogni file rilevati. Questa riga è riportato un esempio di un nome di file, vale a dire, `[TestApp.csproj]`. L'IDE prevede le due righe seguenti. Non, tuttavia, definisce lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name`.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Non è disponibile alcun delimitatore finale a questa sezione. Il nome del file, nonché tutti i valori letterali presenti nel file sono definiti nel file di intestazione scc.h. Per altre informazioni, vedere [stringhe usate come chiavi per la ricerca del plug-in un controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Vedere anche
- [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)
- [Stringhe usate come chiavi per la ricerca del plug-in un controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)