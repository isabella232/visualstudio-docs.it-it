---
title: Avvisi di VSInstr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 300088cb8051f53f5f1afbfe41be92dac9853b53
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54834323"
---
# <a name="vsinstr-warnings"></a>Avvisi di VSInstr
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tabella seguente elenca gli avvisi generati dallo strumento VSInstr.exe. Per impedire la visualizzazione dei messaggi, è possibile usare l'opzione NOWARN insieme al numero di avviso appropriato.  
  
|Numero di avviso|Descrizione|  
|--------------------|-----------------|  
|**VSP2000**|Errore interno Impossibile ottenere il nome del file di modulo per questo eseguibile.|  
|**VSP2001**|\<nome assembly> è un assembly con nome sicuro. Deve essere firmato di nuovo prima dell'esecuzione.<br /><br /> Questo avviso viene visualizzato quando un assembly firmato viene instrumentato. È possibile usare lo strumento sn.exe per firmare nuovamente il file binario o disattivare temporaneamente il requisito del nome sicuro. Per altre informazioni, vedere [Sn.exe (Strong Name Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).|  
|**VSP2002**|Impossibile trovare la funzione \<nome funzione> nel file \<nome file><br /><br /> Questo avviso viene visualizzato quando non è possibile individuare una funzione nel file specificato.|  
|**VSP2003**|Impossibile trovare cross-jump alla funzione \<nome funzione> nel file \<nome file>.<br /><br /> Questo avviso viene visualizzato se VSInstr non è in grado di annullare i cross-jump, che vengono usati per l'ottimizzazione del codice.|  
|**VSP2004**|La funzione \<nome funzione> è stata esclusa mediante l'opzione della riga di comando EXCLUDE, ma era una funzione richiesta in quanto contenente un cross-jump.<br /><br /> Questo avviso viene visualizzato se la funzione è stata esclusa mediante l'opzione EXCLUDE, ma è necessaria nel corso del processo di strumentazione. Il profiler include automaticamente la funzione richiesta.|  
|**VSP2005**|Errore interno di strumentazione \<testo errore><br /><br /> Questo avviso viene generato se non è possibile eseguire la strumentazione. Esaminare il testo dell'errore per stabilire se è possibile correggerlo.|  
|**VSP2006**|Impossibile individuare il PDB per \<nome><br /><br /> Questo avviso viene visualizzato se il file PDB non è presente nel percorso di ricerca o non corrisponde al file binario.|  
|**VSP2007**|\<nome file> non contiene codice instrumentabile.<br /><br /> Questo avviso viene generato se le funzioni presenti nel file binario sono state tutte escluse o se il file specificato contiene solo risorse.|  
|**VSP2008**|Impossibile ottenere gli attributi di sicurezza da \<nome>. Codice di errore \<codice><br /><br /> Questo avviso viene visualizzato se l'utente non dispone dell'autorizzazione READ_DAC. Durante il processo di strumentazione, il profiler tenta di mantenere l'elenco DACL originale per il file binario. Poiché il file binario originale viene sostituito con uno nuovo, l'elenco DACL del file originale deve essere copiato e applicato al nuovo file binario. Questa operazione può avere esito negativo se l'utente non dispone dell'accesso READ_DAC per il file binario originale.|  
|**VSP2009**|Impossibile impostare gli attributi di sicurezza per \<nome>. Codice di errore \<numero errore><br /><br /> Questo avviso viene visualizzato se l'utente non dispone dell'autorizzazione WRITE_DAC. Durante il processo di strumentazione, il profiler tenta di mantenere l'elenco DACL originale per il file binario. Poiché il file binario originale viene sostituito con uno nuovo, l'elenco DACL del file originale deve essere copiato e applicato al nuovo file binario. Questa operazione può avere esito negativo se l'utente non dispone dell'accesso WRITE_DAC per il nuovo file binario.|  
|**VSP2010**|Nessuna funzione selezionata in modo specifico per la strumentazione a causa delle opzioni -INCLUDE/-EXCLUDE|  
|**VSP2011**|Funcspec Include/Exclude \<nome> non corrispondente ad alcuna funzione|  
|**VSP2012**|The image does not contain any code that can be instrumented for code coverage. (L'immagine non contiene codice che può essere instrumentato per il code coverage.)<br /><br /> Il profiler non esegue la strumentazione del tipo di codice seguente:<br /><br /> -   Funzioni CRT statiche<br />-   Metodi gestiti attribuiti con NonUserCodeAttribute<br />-   Metodi gestiti attribuiti con DebuggerHiddenAttribute<br />-   Blocchi MASM<br /><br /> Questo avviso viene generato se, dopo l'applicazione di filtri, non rimane codice.|  
|**VSP2013**|La strumentazione di questa immagine ne richiede l'esecuzione come processo a 32 bit. I flag dell'intestazione CLR sono stati aggiornati di conseguenza.<br /><br /> Il profiler modifica il file binario in modo che i sistemi operativi a 64 bit possano aprire il processo a 32 bit nell'emulatore WOW64. Questa operazione può avere esito negativo per le librerie (DLL) caricate in un processo a 64 bit esistente. L'avviso in questione notifica la dipendenza all'utente.|  
|**VSP2014**|L'immagine instrumentata risultante sembra non valida e potrebbe non essere eseguita.<br /><br /> Questo messaggio viene visualizzato quando l'assembly instrumentato finale presenta un'intestazione PE non valida.|  
  
## <a name="see-also"></a>Vedere anche  
 [VSInstr](../profiling/vsinstr.md)
