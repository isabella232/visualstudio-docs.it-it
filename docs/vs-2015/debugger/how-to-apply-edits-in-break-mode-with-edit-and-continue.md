---
title: 'Procedura: Applicare modifiche in modalità di interruzione con modifica e continuazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd247cd50566130504110bd37c4b87f9e4783ae7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969040"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Procedura: Applicare modifiche in modalità di interruzione con modifica e continuazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare Modifica e continuazione per modificare il codice in modalità di interruzione e continuare senza interrompere e riavviare l'esecuzione.  
  
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:  
  
-   Debug in modalità mista (nativo/gestito).  
  
-   Debug SQL.  
  
-   Debug di un dump di Dr. Watson.  
  
-   Modifica di codice dopo un'eccezione non gestita, quando l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.  
  
-   Debug di un'applicazione di runtime incorporata.  
  
-   Debug di un'applicazione con **Collega a** anziché tramite l'esecuzione dell'applicazione con **avviare** dal **Debug** menu.  
  
-   Debug di codice ottimizzato.  
  
-   Debug di codice gestito quando la destinazione è un'applicazione a 64 bit. Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86 (_Project_**delle proprietà**, **compilare** scheda **del compilatore avanzate** impostazione.).  
  
-   Debug di una versione precedente del codice dopo un tentativo non riuscito di compilazione di una nuova versione a causa della presenza di errori di compilazione.  
  
### <a name="to-edit-code-in-break-mode"></a>Per modificare il codice in modalità di interruzione  
  
1.  Attivare la modalità di interruzione in uno dei seguenti modi:  
  
    -   Impostare un punto di interruzione nel codice, quindi scegliere **Avvia debug** dal menu **Debug** e attendere che l'applicazione raggiunga il punto di interruzione.  
  
         - oppure -  
  
    -   Avviare il debug, quindi scegliere **Interrompi tutto** dal menu **Debug**.  
  
         - oppure -  
  
    -   Quando si verifica un'eccezione, scegliere **Abilita modifica** nel**informazioni sulle eccezioni**.  
  
2.  Apportare tutte le modifiche desiderate al codice, purché siano valide.  
  
     Per altre informazioni, vedere [modifiche non supportate in Visual Basic modifica e continuazione](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Se si tenta di apportare una modifica non consentita da Modifica e continuazione, la modifica verrà contrassegnata con una riga ondulata di colore viola e nell'Elenco attività verrà indicata un'attività da eseguire. Per poter proseguire l'esecuzione del codice, è necessario annullare la modifica non valida del codice.  
  
3.  Scegliere **Continua** dal menu **Debug** per riprendere l'esecuzione.  
  
     Il codice verrà eseguito con le modifiche incorporate nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuano di modifiche non supportate in Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Modifica e continuazione (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
