---
title: MSSCCPRJ. File SCC | Microsoft Docs
description: Informazioni su MSSCCPRJ. File SCC, ovvero un file locale sul lato client usato dal plug-in controllo del codice sorgente, che funziona con l'SDK Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 74a83ff3160ebe12fd16a811b6580061c0572f75
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158541"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. File SCC
Quando si posiziona una Visual Studio o un progetto nel controllo del codice sorgente usando l'IDE, l'IDE riceve due informazioni chiave. Le informazioni provengono dal plug-in del controllo del codice sorgente sotto forma di stringhe. Queste stringhe, "AuxPath" e "ProjName", sono opache nell'IDE, ma vengono usate dal plug-in per individuare la soluzione o il progetto nel controllo della versione. L'IDE ottiene in genere queste stringhe la prima volta chiamando [SccGetProjPath](../extensibility/sccgetprojpath-function.md)e quindi le salva nel file di soluzione o di progetto per le chiamate future a [SccOpenProject](../extensibility/sccopenproject-function.md). Se incorporate nei file di soluzione e di progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente crea rami, fork o copia i file di soluzione e di progetto presenti nel controllo della versione. Per assicurarsi che i file di soluzione e di progetto puntino al percorso corretto nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe sono destinate a essere opache, potrebbe non essere sempre chiaro come devono essere aggiornate.

 Il plug-in del controllo del codice sorgente può evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato file *MSSCCPRJ.SCC.* Si tratta di un file locale sul lato client di proprietà e gestito dal plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma viene generato dal plug-in per ogni directory che contiene file controllati dal codice sorgente. Per determinare quali file sono Visual Studio file di soluzione e di progetto, un plug-in di controllo del codice sorgente può confrontare le estensioni di file con un elenco standard o fornito dall'utente. Quando l'IDE rileva che un plug-in supporta il file *MSSCCPRJ.SCC,* smette di incorporare le stringhe "AuxPath" e "ProjName" nei file di soluzione e di progetto e legge invece tali stringhe dal file *MSSCCPRJ.SCC.*

 Un plug-in di controllo del codice sorgente che supporta il file *MSSCCPRJ.SCC* deve rispettare le linee guida seguenti:

- Può essere presente un solo file *MSSCCPRJ.SCC* per ogni directory.

- Un file *MSSCCPRJ.SCC* può contenere "AuxPath" e "ProjName" per più file sotto controllo del codice sorgente all'interno di una determinata directory.

- La stringa "AuxPath" non deve contenere virgolette. È consentito contenere virgolette come delimitatori(ad esempio, una coppia di virgolette doppie può essere usata per indicare una stringa vuota). L'IDE rimuoverà tutte le virgolette dalla stringa "AuxPath" quando viene letta dal file *MSSCCPRJ.SCC.*

- Stringa "ProjName" in *MSSCCPRJ. Il file SCC* deve corrispondere esattamente alla stringa restituita dalla `SccGetProjPath` funzione. Se la stringa restituita dalla funzione contiene virgolette, la stringa nel file *MSSCCPRJ.SCC* deve contenere virgolette e viceversa.

- Un file *MSSCCPRJ.SCC* viene creato o aggiornato ogni volta che un file viene inserito nel controllo del codice sorgente.

- Se un file *MSSCCPRJ.SCC* viene eliminato, un provider deve rigenerarlo alla successiva esecuzione di un'operazione di controllo del codice sorgente relativa a tale directory.

- Un file *MSSCCPRJ.SCC* deve seguire rigorosamente il formato definito.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Illustrazione di MSSCCPRJ. Formato di file SCC
 Di seguito è riportato un esempio del formato di file *MSSCCPRJ.SCC* (i numeri di riga vengono forniti solo come guida e non devono essere inclusi nel corpo del file):

- [Riga 1] `SCC = This is a Source Code Control file`

- [Riga 2]

- [Riga 3] `[TestApp.sln]`

- [Riga 4] `SCC_Aux_Path = "\\server\vss\"`

- [Riga 5] `SCC_Project_Name = "$/TestApp"`

- [Riga 6]

- [Riga 7] `[TestApp.csproj]`

- [Riga 8] `SCC_Aux_Path = "\\server\vss\"`

- [Riga 9] `SCC_Project_Name = "$/TestApp"`

 La prima riga indica lo scopo del file e funge da firma per tutti i file di questo tipo. Questa riga dovrebbe essere simile alla seguente in tutti i *file MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 Nella sezione seguente vengono fornite informazioni dettagliate sulle impostazioni per ogni file, contrassegnate dal nome del file tra parentesi quadre. Questa sezione viene ripetuta per ogni file monitorato. Questa riga è un esempio di nome di file, ad esempio `[TestApp.csproj]` . L'IDE prevede le due righe seguenti. Non definisce tuttavia lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 In questa sezione non è presente alcun delimitatore finale. Il nome del file, nonché tutti i valori letterali visualizzati nel file, sono definiti nel file di intestazione scc.h. Per altre informazioni, vedere [Stringhe usate come chiavi per trovare un plug-in del controllo del codice sorgente.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Stringhe usate come chiavi per trovare un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
