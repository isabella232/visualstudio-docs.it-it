---
title: Descrizione directory modello (. Vsdir) File | Microsoft Docs
description: Informazioni su come un file di descrizione della directory modello consente Visual Studio IDE di visualizzare cartelle, file vsz e modelli associati al progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 70ee15328b6f89c5df5323951a11a0ce26d9d2393d25ced6b6434c098354a19e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431825"
---
# <a name="template-directory-description-vsdir-files"></a>File (con estensione vsdir) di descrizione della directory dei modelli
Un file di descrizione della directory modello (con estensione vsdir) è un file di testo che consente all'ambiente di sviluppo integrato (IDE) di visualizzare cartelle, file vsz della procedura guidata e file modello associati al progetto nelle finestre di dialogo. Il contenuto include un record per ogni file o cartella. Tutti i file con estensione vsdir in un percorso di riferimento vengono uniti, anche se viene in genere fornito un solo file vsdir per descrivere più cartelle, procedure guidate o file modello.

 Le cartelle (sottodirectory), i file a cui viene fatto riferimento nel file vsdir e il file vsdir stesso si trovano tutti nella stessa directory. Quando l'IDE esegue una procedura guidata o visualizza una  cartella o un file nelle finestre di dialogo Nuovo **Project** o Aggiungi nuovo elemento, l'IDE esamina la directory che contiene i file eseguiti per determinare se è presente un file vsdir. Se viene trovato un file vsdir, l'IDE lo legge per determinare se contiene una voce per la cartella o il file eseguito o visualizzato. Se viene trovata una voce, l'IDE usa le informazioni nell'esecuzione della procedura guidata o nella visualizzazione del contenuto.

 L'esempio di codice seguente deriva dal file SourceFiles.vsdir nella chiave del Registro di sistema \<EnvSDK> \BscPrj\BscPrj\BscPrjProjectItems\Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 In questo caso, due record sono in un unico file. Una nuova riga (carattere di ritorno a capo) separa ogni record. Ogni riga rappresenta un tipo di file diverso. Un carattere barra verticale (&#124;) separa i campi in ogni record. Una singola directory può contenere più file con estensione vsdir con nomi di file diversi oppure è possibile avere un file vsdir per ogni tipo di file.

## <a name="fields"></a>Campi
 Nella tabella seguente sono elencati i campi specificati per ogni record.

| Campo | Descrizione |
| - | - |
| Nome percorso relativo (RelPathName) | Nome della cartella, del modello o del file vsz, ad esempio HeaderFile.h o MyWizard.vsz. Questo campo può anche essere un nome usato per rappresentare una cartella. |
| {clsidPackage} | GUID del VSPackage che consente l'accesso alle stringhe localizzate, ad esempio LocalizedName, Description, IconResourceId e SuggestedBaseName, nelle risorse della libreria a collegamento dinamico satellite (DLL) del pacchetto VSPackage. IconResourceId si applica se DLLPath non viene fornito. **Nota:**  Questo campo è facoltativo a meno che uno o più campi precedenti non siano un identificatore di risorsa. Questo campo è in genere vuoto per i file vsdir che corrispondono a procedure guidate di terze parti che non localizzano il testo. |
| LocalizedName | Nome localizzato del file modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questo nome viene visualizzato nella finestra **di dialogo Aggiungi** nuovo elemento . **Nota:**  Se LocalizedName è un identificatore di risorsa, è necessario {clsidPackage}. |
| SortPriority | Intero che rappresenta la priorità relativa di questo file modello o procedura guidata. Ad esempio, se questo elemento ha un valore pari a 1, questo elemento viene visualizzato accanto ad altri elementi con valore 1 e prima di tutti gli elementi con un valore di ordinamento pari a 2 o superiore.<br /><br /> La priorità di ordinamento è relativa agli elementi nella stessa directory. Nella stessa directory possono essere presenti più file con estensione vsdir. In tal caso, gli elementi di tutti <em>gli oggetti .</em> I file vsdir in tale directory vengono uniti. Gli elementi con la stessa priorità vengono elencati in ordine lessicografico senza distinzione tra maiuscole e minuscole del nome visualizzato. La `_wcsicmp` funzione viene usata per ordinare gli elementi.<br /><br /> Gli elementi non descritti nei file vsdir includono un numero di priorità maggiore del numero di priorità più alto elencato nei file con estensione vsdir. Il risultato è che questi elementi si trova alla fine dell'elenco visualizzato indipendentemente dal nome. |
| Descrizione | Descrizione localizzata del file modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questa stringa viene visualizzata nella **finestra di dialogo Project** o Aggiungi nuovo **elemento** quando l'elemento è selezionato. |
| DLLPath o {clsidPackage} | Usato per caricare un'icona per il file modello o la procedura guidata. L'icona viene caricata come risorsa da un file .dll o .exe usando IconResourceId. Questo .dll o .exe può essere identificato usando un percorso completo o usando un GUID di un VSPackage. La DLL di implementazione del pacchetto VSPackage viene usata per caricare l'icona (non la DLL satellite). |
| IconResourceId | Identificatore di risorsa nella DLL o nella DLL di implementazione vsPackage che determina l'icona da visualizzare. |
| Flag ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Usato per disabilitare o abilitare i **campi Nome** **e Percorso** nella finestra **di** dialogo Aggiungi nuovo elemento. Il valore del campo **Flags** è l'equivalente decimale della combinazione di flag di bit obbligatori.<br /><br /> Quando un utente seleziona un  elemento nella scheda Nuovo, il progetto determina se  il campo Nome e il campo Posizione vengono visualizzati quando viene visualizzata per la prima volta la finestra di dialogo Aggiungi nuovo elemento. Un elemento, tramite un file vsdir, può controllare solo se i campi sono abilitati o disabilitati quando l'elemento è selezionato. |
| SuggestedBaseName | Rappresenta il nome predefinito per il file, la procedura guidata o il modello. Questo campo è una stringa o un identificatore di risorsa nel formato "#ResID". L'IDE usa questo valore per fornire un nome predefinito per l'elemento. A questo valore di base viene aggiunto un valore intero per rendere univoco il nome, ad esempio MyFile21.asp.<br /><br /> Nell'elenco precedente, Description, DLLPath, IconResourceId, Flags e SuggestedBaseNumber si applicano solo ai file del modello e della procedura guidata. Questi campi non si applicano alle cartelle. Questo fatto è illustrato nel codice nel file BscPrjProjectItems nella chiave del Registro di sistema \<EnvSDK> \BscPrj\BscPrj\BscPrjProjectItems. Questo file contiene tre record (uno per ogni cartella) con quattro campi per ogni record: RelPathName, {clsidPackage}, LocalizedName e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Quando si crea un file della procedura guidata, è necessario considerare anche i problemi seguenti.

- Qualsiasi campo non obbligatorio per cui non sono presenti dati significativi deve contenere uno 0 (zero) come segnaposto.

- Se non viene specificato alcun nome localizzato, nel file della procedura guidata viene usato il nome del percorso relativo.

- DLLPath esegue l'override di clsidPackage per il percorso dell'icona.

- Se non viene definita alcuna icona, l'IDE sostituisce l'icona predefinita per un file con tale estensione.

- Se non viene specificato alcun nome di base suggerito, viene Project'.

- Se si eliminano i file vsz, le cartelle o i file modello, è necessario rimuovere anche i record associati dal file vsdir.

## <a name="see-also"></a>Vedi anche
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
