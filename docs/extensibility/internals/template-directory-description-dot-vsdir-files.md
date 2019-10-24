---
title: Descrizione Directory modello (. File VSDIR) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb20a1fbc8d5edd9783521fa933dbddc74ac2a22
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722823"
---
# <a name="template-directory-description-vsdir-files"></a>File (con estensione vsdir) di descrizione della directory dei modelli
Un file di descrizione della directory dei modelli (. vsdir) è un file di testo che consente all'Integrated Development Environment (IDE) di visualizzare le cartelle, i file con estensione vsz della procedura guidata e i file modello associati al progetto nelle finestre di dialogo. Il contenuto include un record per ogni file o cartella. Viene eseguito il merge di tutti i file con estensione VSDIR in un percorso a cui viene fatto riferimento, anche se in genere viene fornito un solo file con estensione VSDIR per descrivere più cartelle, procedure guidate o file di modello.

 Le cartelle (sottodirectory), i file a cui viene fatto riferimento nel file con estensione VSDIR e il file con estensione VSDIR si trovano tutti nella stessa directory. Quando l'IDE esegue una procedura guidata o Visualizza una cartella o un file nelle finestre di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** , l'IDE esamina la directory che contiene i file eseguiti per determinare se è presente un file con estensione VSDIR. Se viene trovato un file con estensione VSDIR, questo viene letto dall'IDE per determinare se contiene una voce per la cartella o il file eseguito o visualizzato. Se viene trovata una voce, l'IDE usa le informazioni nell'esecuzione della procedura guidata o la visualizzazione del contenuto.

 L'esempio di codice seguente viene dal file SourceFiles. vsdir nella chiave del registro \<EnvSDK di sistema > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 In questo caso, due record si trovano in un unico file. Una nuova riga (carattere di ritorno a capo) separa ogni record. Ogni riga rappresenta un tipo di file diverso. Un carattere pipe&#124;() separa i campi in ogni record. Una singola directory può contenere più file con estensione VSDIR con nomi di file diversi oppure è possibile disporre di un file con estensione VSDIR per ogni tipo di file.

## <a name="fields"></a>Campi
 Nella tabella seguente sono elencati i campi specificati per ogni record.

| Campo | Descrizione |
| - | - |
| Nome percorso relativo (RelPathName) | Nome della cartella, del modello o del file con estensione vsz, ad esempio HeaderFile. h o la procedura guidata. vsz. Questo campo può essere anche un nome utilizzato per rappresentare una cartella. |
| ClsidPackage | GUID del pacchetto VSPackage che consente l'accesso alle stringhe localizzate, ad esempio Localizzated, Description, IconResourceId e SuggestedBaseName, nelle risorse della libreria di collegamento dinamico (DLL) satellite del VSPackage. IconResourceId si applica se non viene specificato DLLPath. **Nota:**  Questo campo è facoltativo a meno che uno o più campi precedenti non siano un identificatore di risorsa. Questo campo è in genere vuoto per i file con estensione VSDIR che corrispondono a procedure guidate di terze parti che non localizzano il testo. |
| LocalizedName | Nome localizzato del file modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questo nome viene visualizzato nella finestra di dialogo **Aggiungi nuovo elemento** . **Nota:**  Se Localizzaname è un identificatore di risorsa, è necessario {clsidPackage}. |
| SortPriority | Integer che rappresenta la priorità relativa del file di modello o della procedura guidata. Se, ad esempio, l'elemento ha un valore pari a 1, questo elemento viene visualizzato accanto ad altri elementi con un valore pari a 1 e un valore superiore a tutti gli elementi con un valore di ordinamento di 2 o superiore.<br /><br /> La priorità di ordinamento è relativa agli elementi nella stessa directory. Nella stessa directory possono essere presenti più file VSDIR. In tal caso, gli elementi di tutti i <em>.</em> i file VSDir in tale directory vengono uniti. Gli elementi con la stessa priorità vengono elencati in ordine lessicografico senza distinzione tra maiuscole e minuscole del nome visualizzato. La funzione `_wcsicmp` viene utilizzata per ordinare gli elementi.<br /><br /> Gli elementi non descritti in file VSDIR includono un numero di priorità maggiore del numero di priorità più elevato elencato nei file con estensione VSDIR. Il risultato è che questi elementi si trovano alla fine dell'elenco visualizzato indipendentemente dal nome. |
| Descrizione | Descrizione localizzata del file modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questa stringa viene visualizzata nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** quando l'elemento è selezionato. |
| DLLPath o {clsidPackage} | Utilizzato per caricare un'icona per il file modello o la procedura guidata. L'icona viene caricata come risorsa da un file con estensione dll o exe utilizzando IconResourceId. Questo file con estensione dll o exe può essere identificato usando un percorso completo o un GUID di un pacchetto VSPackage. La DLL di implementazione del pacchetto VSPackage viene utilizzata per caricare l'icona (non la DLL satellite). |
| IconResourceId | Identificatore di risorsa nella DLL di implementazione della DLL o del pacchetto VSPackage che determina l'icona da visualizzare. |
| Flag (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Consente di disabilitare o abilitare i campi **nome** e **percorso** nella finestra di dialogo **Aggiungi nuovo elemento** . Il valore del campo **Flags** è l'equivalente decimale della combinazione dei flag di bit richiesti.<br /><br /> Quando un utente seleziona un elemento nella **nuova** scheda, il progetto determina se il campo nome e il campo percorso vengono visualizzati quando la finestra di dialogo **Aggiungi nuovo elemento** viene visualizzata per la prima volta. Un elemento, tramite un file VSDIR, può controllare solo se i campi sono abilitati o disabilitati quando l'elemento è selezionato. |
| SuggestedBaseName | Rappresenta il nome predefinito per il file, la procedura guidata o il modello. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". L'IDE utilizza questo valore per fornire un nome predefinito per l'elemento. Il valore di base viene aggiunto con un valore integer per rendere univoco il nome, ad esempio MyFile21. ASP.<br /><br /> Nell'elenco precedente descrizione, DLLPath, IconResourceId, Flags e SuggestedBaseNumber sono validi solo per i file di modello e di procedura guidata. Questi campi non si applicano alle cartelle. Questo fatto viene illustrato nel codice del file BscPrjProjectItems nel \<EnvSDK > chiave del registro di sistema \BscPrj\BscPrj\BscPrjProjectItems. Questo file contiene tre record (uno per ogni cartella) con quattro campi per ogni record: RelPathName, {clsidPackage}, Localizzaname e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Quando si crea un file della procedura guidata, è necessario considerare anche i seguenti problemi.

- Qualsiasi campo non obbligatorio per il quale non sono presenti dati significativi deve contenere uno 0 (zero) come segnaposto.

- Se non viene specificato alcun nome localizzato, il nome del percorso relativo viene utilizzato nel file della procedura guidata.

- DLLPath esegue l'override di clsidPackage per la posizione dell'icona.

- Se non è stata definita alcuna icona, l'IDE sostituisce l'icona predefinita per un file con tale estensione.

- Se non viene specificato alcun nome di base suggerito, viene utilizzato ' Project '.

- Se si eliminano i file con estensione vsz, le cartelle o i file modello, è necessario rimuovere anche i record associati dal file VSDIR.

## <a name="see-also"></a>Vedere anche
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)