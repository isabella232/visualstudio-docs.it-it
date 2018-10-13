---
title: 'Procedura: Debug di codice ottimizzato | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e278464dcdf3fd7b030f59de1eaccbfed4ee36eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175422"
---
# <a name="how-to-debug-optimized-code"></a>Procedura: eseguire il debug di codice ottimizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Il [/Zo (ottimizzare il debug)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)l'opzione del compilatore (introdotta in Visual Studio Update 3) genera informazioni di debug più complete per il codice ottimizzato (progetti non compilati con la **/Od** opzione del compilatore. Visualizzare [Opzioni /O (Ottimizza codice)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). Questo include un supporto migliorato per il debug delle variabili locali e delle funzioni inline.  
>   
>  [Modifica e continuazione](../debugger/edit-and-continue-visual-csharp.md) è disabilitata quando il **/Zo** viene usata l'opzione.  
  
 Quando il compilatore ottimizza il codice, modifica la posizione e l'organizzazione delle istruzioni. IL risultato è un codice compilato più efficace. A causa di questa ridisposizione, il debugger non è sempre in grado di identificare il codice sorgente corrispondente a un set di istruzioni.  
  
 L'ottimizzazione del codice può influenzare:  
  
-   Le variabili locali, che possono essere rimosse o spostate in posizioni non riconosciute dal debugger  
  
-   Le posizioni all'interno di una funzione, che vengono modificate quando l'utilità di ottimizzazione esegue l'unione di blocchi di codice.  
  
-   I nomi delle funzioni per i frame nello stack di chiamate, che potrebbero risultare errati se due funzioni vengono unite.  
  
 I frame visualizzati nello stack di chiamate sono in genere corretti, se si dispone di simboli per ciascuno di essi. I frame nello stack di chiamate risulteranno errati se lo stack è danneggiato, se sono presenti funzioni scritte in linguaggio assembly oppure se esistono frame del sistema operativo privi di simboli corrispondenti nello stack di chiamate.  
  
 Le variabili globali e di tipo statico vengono visualizzate sempre correttamente, analogamente al layout delle strutture. Se si dispone di un puntatore a una struttura e il valore di questo puntatore è corretto, tutte le variabili membro della struttura conterranno il valore corretto.  
  
 A causa di queste limitazioni, è opportuno eseguire il debug usando, se possibile, una versione del programma non ottimizzata. Per impostazione predefinita l'ottimizzazione è disattivata nella configurazione Debug di un programma Visual C++ e attivata nella configurazione Release.  
  
 Può tuttavia accadere che un bug venga individuato solo nella versione ottimizzata di un programma. In tal caso è necessario effettuare il debug del codice ottimizzato.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Per attivare l'ottimizzazione nella configurazione di una build di debug  
  
1.  Quando si crea un nuovo progetto, selezionare la destinazione `Win32 Debug`. Usare la `Win32``Debug` di destinazione fino a quando non viene completato il debug del programma e si è pronti per compilare un `Win32 Release` destinazione. Il compilatore non ottimizza la destinazione `Win32 Debug`.  
  
2.  Selezionare il progetto in Esplora soluzioni.  
  
3.  Nel **View** menu, fare clic su **pagine delle proprietà**.  
  
4.  Nel **pagine delle proprietà** finestra di dialogo, assicurarsi `Debug` sia selezionato nel **configurazione** elenco a discesa.  
  
5.  Nella visualizzazione di cartelle a sinistra, selezionare la **C/C++** cartella.  
  
6.  Sotto il **C++** cartella, selezionare `Optimization`.  
  
7.  Nell'elenco di proprietà situato a destra cercare `Optimization`. L'impostazione accanto a esso probabilmente afferma `Disabled (` [/Od](http://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5)`)`. Scegliere una delle altre opzioni (`Minimum Size``(`[/O1](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Maximum Speed``(` [/O2](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Full Optimization``(` [/Ox](http://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760) `)`, o `Custom`).  
  
8.  Se si è scelto l'opzione `Custom` per `Optimization`, a questo punto è possibile impostare le opzioni per le altre proprietà presenti nell'elenco.  
  
9. Selezionare la proprietà di configurazione, C/C++, il nodo della riga di comando della pagina delle proprietà del progetto e aggiungere `(` [/Zo](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` per il **opzioni aggiuntive** casella di testo.  
  
    > [!WARNING]
    >  `/Zo` richiede Visual Studio 2013 Update 3 o una versione successiva.  
    >   
    >  Aggiunta `/Zo` disabiliterà [modifica e continuazione](../debugger/edit-and-continue-visual-csharp.md).  
  
 Quando si esegue il debug di codice ottimizzato, usare il **Disassembly** finestra per visualizzare le istruzioni che vengono effettivamente create ed eseguite. Nell'impostazione di punti di interruzione, è necessario sapere che un punto di interruzione può essere spostato insieme a un'istruzione. Si consideri il codice di esempio seguente:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Si supponga di impostare un punto di interruzione in questa riga. Ci si aspetterebbe che il punto di interruzione venga raggiunto 10 volte, ma se il codice è ottimizzato, il punto di interruzione verrà raggiunto solo una volta. Ciò è dovuto al fatto che la prima istruzione imposta il valore di `x` su 0. Il compilatore riconosce che questa operazione deve essere eseguita solo una volta ed esce dal ciclo. Il punto di interruzione si sposta con essa. Le istruzioni che confrontano e incrementano `x` rimangono all'interno del ciclo. Quando si visualizza il **Disassembly** finestra, il [unità incremento](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) viene impostata automaticamente su istruzione per un maggiore controllo, che risulta utile se si esegue il codice ottimizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



