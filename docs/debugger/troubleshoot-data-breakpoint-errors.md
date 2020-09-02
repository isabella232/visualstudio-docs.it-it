---
title: Errore-Impossibile impostare il punto di interruzione dei dati | Microsoft Docs
ms.date: 12/3/2019
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
ms.openlocfilehash: 20e3ea1cb0124e6bdfb93e023021673ca2e34602
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248746"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Risoluzione degli errori dei punti di interruzione dei dati
In questa pagina viene illustrata la risoluzione degli errori comuni riscontrati durante l'utilizzo di "Interrompi in caso di modifica del valore"

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnosi degli errori di "Impossibile impostare il punto di interruzione dei dati"
> [!IMPORTANT]
> I punti di interruzione dei dati gestiti sono supportati in .NET Core 3,0 e in alto. È possibile scaricare la versione più recente [qui](https://dotnet.microsoft.com/download).

Di seguito è riportato un elenco di errori che possono verificarsi quando si usano i punti di interruzione dei dati gestiti. Contengono una spiegazione aggiuntiva sul motivo per cui si verifica l'errore e sulle possibili soluzioni o soluzioni alternative per risolvere l'errore.

- *"La versione di .NET usata dal processo di destinazione non supporta i punti di interruzione dei dati. I punti di interruzione dei dati richiedono .NET Core 3.0 + in esecuzione su x86 o x64. "*

  - Il supporto per i punti di interruzione dei dati gestiti inizia con .NET Core 3,0. Attualmente non è supportato in .NET Framework o versione di .NET Core in 3,0. 
    
  - **Soluzione**: per risolvere il problema, aggiornare il progetto a .net core 3,0.

- *"Non è possibile trovare il valore nell'heap gestito e non è possibile tenerne traccia."*
  - Variabile dichiarata nello stack.
    - Non è supportata l'impostazione di punti di interruzione dei dati per le variabili create nello stack perché questa variabile non sarà valida dopo la chiusura della funzione.
    - **Soluzione temporanea**: impostare punti di interruzione nelle righe in cui viene utilizzata la variabile.

  - "Break when value changes" su una variabile non espansa da un elenco a discesa.
    - È necessario che il debugger conosca internamente l'oggetto contenente il campo di cui si vuole tenere traccia. Il Garbage Collector può spostare l'oggetto nell'heap, in modo che il debugger debba essere a conoscenza dell'oggetto che contiene la variabile di cui si vuole tenere traccia. 
    - **Soluzione temporanea**: se ci si trova in un metodo all'interno dell'oggetto in cui si desidera impostare un punto di interruzione dei dati, passare a un frame e utilizzare la `locals/autos/watch` finestra per espandere l'oggetto e impostare un punto di interruzione dei dati nel campo desiderato.

- *"I punti di interruzione dei dati non sono supportati per i campi statici o le proprietà statiche".*
    
  - Al momento non sono supportati proprietà e campi statici. Se si è interessati a questa funzionalità, fornire [commenti e suggerimenti](#provide-feedback).

- *"I campi e le proprietà degli struct non possono essere rilevati".*

  - I campi e le proprietà degli struct non sono supportati al momento. Se si è interessati a questa funzionalità, fornire [commenti e suggerimenti](#provide-feedback).

- *"Il valore della proprietà è stato modificato e non può più essere rilevato".*

  - Una proprietà può modificare il modo in cui viene calcolata in fase di esecuzione e, in tal caso, il numero di variabili da cui dipende la proprietà aumenta e può superare il limite dell'hardware. Vedere `"The property is dependent on more memory than can be tracked by the hardware."` di seguito.

- *"La proprietà dipende da una quantità di memoria superiore a quella che può essere rilevata dall'hardware".*
    
  - Ogni architettura dispone di un numero impostato di byte e di punti di interruzione dei dati hardware che può supportare e la proprietà per cui si desidera impostare un punto di interruzione dei dati ha superato tale limite. Per informazioni sul numero di punti di interruzione dei dati supportati dall'hardware e dei byte disponibili per l'architettura in uso, vedere la tabella relativa alle limitazioni hardware per i punti di [interruzione dei dati](#data-breakpoint-hardware-limitations) . 
  - **Soluzione temporanea**: impostare un punto di interruzione dei dati su un valore che può essere modificato all'interno della proprietà.

- *"I punti di interruzione dei dati non sono supportati quando si utilizza l'analizzatore di espressioni C# legacy".*

  - I punti di interruzione dei dati sono supportati solo nell'analizzatore di espressioni C# non legacy. 
  - **Soluzione**: per disabilitare l'analizzatore di espressioni C# legacy, `Debug -> Options` scegliere `Debugging -> General` deseleziona `"Use the legacy C# and VB expression evaluators"` .

## <a name="data-breakpoint-hardware-limitations"></a>Limitazioni hardware del punto di interruzione dei dati

L'architettura (configurazione della piattaforma) in cui viene eseguito il programma dispone di un numero limitato di punti di interruzione dei dati hardware che possono essere utilizzati. La tabella seguente indica il numero di registri disponibili per l'uso in base all'architettura.

| Architecture | Numero di punti di interruzione dei dati supportati dall'hardware | Dimensioni massime in byte|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Fornire commenti e suggerimenti

Per eventuali problemi o suggerimenti relativi a questa funzionalità, inviare commenti tramite la guida > inviare commenti e suggerimenti > [segnalare un problema](../ide/how-to-report-a-problem-with-visual-studio.md) nell'IDE o nella [community degli sviluppatori](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>Vedere anche

- [Uso di "break when value changes" in .NET Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: Interrompi quando viene modificato il valore: punti di interruzione dei dati per .NET Core in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
