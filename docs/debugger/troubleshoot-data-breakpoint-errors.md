---
title: Impossibile impostare il punto di interruzione dei dati | Microsoft Docs
description: Trovare spiegazioni, soluzioni e soluzioni alternative per "Impossibile impostare gli errori dei punti di interruzione dei dati" che si verificano quando si usa "Interrompi quando il valore cambia".
ms.custom: SEO-VS-2020
ms.date: 5/19/2020
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 73e7e02d90e2a89c81b5e690718c95fe7efe0fb3
ms.sourcegitcommit: 6e27b1238a8aa704b127eac34f4173e9d56690c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "110231965"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Risoluzione degli errori dei punti di interruzione dei dati
Questa pagina illustra come risolvere gli errori comuni rilevati quando si usa "Interrompi quando il valore cambia"

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnosi degli errori "Impossibile impostare il punto di interruzione dei dati"
> [!IMPORTANT]
> I punti di interruzione dei dati gestiti sono supportati in .NET Core 3.0 e versioni seguenti e .NET 5.0.3 e versioni seguenti. È possibile scaricare la versione più [recente qui.](https://dotnet.microsoft.com/download)

Di seguito è riportato un elenco di errori che possono verificarsi quando si usano punti di interruzione dei dati gestiti. Contengono una spiegazione più dettagliata del motivo per cui si verifica l'errore e possibili soluzioni o soluzioni alternative per risolvere l'errore.

- *"La versione di .NET usata dal processo di destinazione non supporta i punti di interruzione dei dati. I punti di interruzione dei dati richiedono .NET Core 3.x o .NET 5.0.3+, in esecuzione in x86 o x64."*

  - Il supporto per i punti di interruzione dei dati gestiti è iniziato in .NET Core 3.0. Attualmente non è supportato in .NET Framework, versioni di .NET Core in 3.0 o versioni di .NET nella versione 5.0.3. 
    
  - **Soluzione:** la soluzione consiste nell'aggiornare il progetto a .NET Core 3.0.

- *"Il valore non è stato trovato nell'heap gestito e non può essere rilevato."*
  - Variabile dichiarata nello stack.
    - Non è possibile impostare punti di interruzione dei dati per le variabili create nello stack perché questa variabile non sarà valida al termine della funzione.
    - **Soluzione** alternativa: impostare punti di interruzione nelle righe in cui viene usata la variabile.

  - "Interrompi quando il valore cambia" in una variabile non espansa da un elenco a discesa.
    - Il debugger deve conoscere internamente l'oggetto contenente il campo di cui si vuole tenere traccia. Il Garbage Collector può spostare l'oggetto nell'heap in modo che il debugger dovrà conoscere l'oggetto che contiene la variabile che si vuole rilevare. 
    - **Soluzione** alternativa: se si usa un metodo all'interno dell'oggetto su cui si vuole impostare un punto di interruzione dei dati, passare a un frame e usare la finestra per espandere l'oggetto e impostare un punto di interruzione dati nel `locals/autos/watch` campo desiderato.

- *"I punti di interruzione dei dati non sono supportati per i campi statici o le proprietà statiche".*
    
  - Le proprietà e i campi statici non sono attualmente supportati. Se si è interessati a questa funzionalità, inviare [commenti e suggerimenti.](#provide-feedback)

- *"Non è possibile tenere traccia dei campi e delle proprietà degli struct".*

  - I campi e le proprietà degli struct non sono attualmente supportati. Se si è interessati a questa funzionalità, inviare [commenti e suggerimenti.](#provide-feedback)

- *"Il valore della proprietà è stato modificato e non può più essere monitorato".*

  - Una proprietà può modificare il modo in cui viene calcolata in fase di esecuzione e, in questo caso, il numero di variabili da cui dipende la proprietà aumenta e può superare la limitazione hardware. Vedere `"The property is dependent on more memory than can be tracked by the hardware."` di seguito.

- *"La proprietà dipende da una quantità di memoria maggiore di quella rilevata dall'hardware".*
    
  - Ogni architettura ha un numero impostato di byte e punti di interruzione dei dati hardware che può supportare e la proprietà su cui si vuole impostare un punto di interruzione dei dati ha superato tale limite. Fare riferimento alla tabella Limitazioni hardware [dei](#data-breakpoint-hardware-limitations) punti di interruzione dei dati per scoprire quanti byte e punti di interruzione dei dati supportati dall'hardware sono disponibili per l'architettura in uso. 
  - **Soluzione** alternativa: impostare un punto di interruzione dei dati su un valore che può cambiare all'interno della proprietà .

- *"I punti di interruzione dei dati non sono supportati quando si usa l'analizzatore di espressioni C# legacy."*

  - I punti di interruzione dei dati sono supportati solo nell'analizzatore di espressioni C# non legacy. 
  - **Soluzione:** disabilitare l'analizzatore di espressioni C# legacy selezionando `Debug -> Options` quindi in `Debugging -> General` deselezionare `"Use the legacy C# and VB expression evaluators"` .

- *"La classe **X ha** una visualizzazione personalizzata del debugger che blocca l'uso di punti di interruzione dei dati solo su dati specifici".*
  
  - I punti di interruzione dei dati sono supportati solo nella memoria creata dal processo di destinazione (l'applicazione di cui è in corso il debug). La memoria su cui viene impostato il punto di interruzione dei dati è stata contrassegnata come probabilmente di proprietà di un oggetto creato da un [attributo DebuggerTypeProxy](using-debuggertypeproxy-attribute.md) o da un altro elemento che non fa parte del processo di destinazione.
  - **Soluzione** alternativa: espandere la "Visualizzazione non elaborata" degli oggetti anziché espandere la visualizzazione DebuggerTypeProxy degli oggetti e quindi impostare il punto di interruzione dei dati. Ciò garantisce che il punto di interruzione dei dati non sia in memoria di proprietà di un oggetto creato da un attributo DebuggerTypeProxy.

## <a name="data-breakpoint-hardware-limitations"></a>Limitazioni hardware dei punti di interruzione dei dati

L'architettura (configurazione della piattaforma) su cui viene eseguito il programma ha un numero limitato di punti di interruzione dei dati hardware che può usare. La tabella seguente indica il numero di registri disponibili da usare per ogni architettura.

| Architettura | Numero di punti di interruzione dati supportati dall'hardware | Dimensioni massime in byte|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Fornire il feedback

Per eventuali problemi o suggerimenti relativi a questa funzionalità, inviare commenti e suggerimenti tramite help > send feedback > [Report a Problem](../ide/how-to-report-a-problem-with-visual-studio.md) in the IDE or in the [Developer Community](https://aka.ms/feedback/suggest?space=8).

## <a name="see-also"></a>Vedi anche

- [Uso di "Interrompi quando il valore cambia" in .NET Core 3.0.](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)
- [DevBlog: Interrompi quando cambia il valore: punti di interruzione dei dati per .NET Core Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
