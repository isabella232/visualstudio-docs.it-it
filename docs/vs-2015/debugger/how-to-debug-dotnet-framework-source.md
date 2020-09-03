---
title: "Procedura: eseguire il debug dell'origine .NET Framework | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205436"
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: debug del codice sorgente di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce nuove funzionalità per il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] debug di. Per eseguire [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] il debug dell'origine, è necessario avere accesso ai simboli di debug per il codice. È anche necessario abilitare l'esecuzione dell'istruzione nell' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origine.  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Nella finestra di dialogo **Opzioni** è possibile attivare il download dei simboli e di avanzamento. Quando si attiva il download dei simboli, è possibile scegliere di scaricarli immediatamente o attivare solo l'opzione per eseguire il download successivamente. Se non si esegue immediatamente il download, i simboli verranno scaricati la volta successiva che si avvia il debug dell'applicazione. È anche possibile scaricare manualmente dalla finestra **moduli** o **stack di chiamate** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Per attivare il debug di origine di .NET Framework   
  
1. Scegliere **Opzioni** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Opzioni** fare clic sulla categoria **debug** .  
  
3. Nella casella **generale** impostare **Abilita .NET Framework** esecuzione del codice sorgente.  
  
    1. Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Fare clic su **OK**.  
  
    2. Se il percorso della cache dei simboli non è impostato, viene visualizzata un'altra finestra di dialogo con un avviso indicante che è stato impostato il percorso predefinito della cache dei simboli. Fare clic su **OK**.  
  
4. Nella categoria **debug** fare clic su **simboli**.  
  
5. Se si desidera modificare il percorso della cache dei simboli:  
  
    1. Aprire il nodo **debug** nella casella a sinistra.  
  
    2. Nel nodo **debug** fare clic su **simboli**.  
  
    3. Modificare il percorso in **memorizza nella cache i simboli dai server di simboli in questa directory** o fare clic su **Sfoglia** per scegliere un percorso.  
  
6. Se si desidera scaricare immediatamente i simboli, fare clic su **Carica simboli utilizzando i percorsi indicati sopra**.  
  
     Questo pulsante non è disponibile nella modalità progettazione.  
  
     Se non si sceglie di scaricare ora i simboli, questi ultimi verranno scaricati automaticamente al successivo avvio del debug del programma.  
  
7. Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni** .  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Per caricare simboli di Framework utilizzando la finestra Moduli  
  
1. Nella finestra **moduli** fare clic con il pulsante destro del mouse su un modulo per il quale non sono caricati i simboli. È possibile stabilire se i simboli vengono caricati o meno osservando la colonna **stato simboli** .  
  
2. Scegliere **Carica simboli da** e fare clic su server dei simboli **Microsoft** per scaricare i simboli dal server dei simboli pubblici Microsoft o dal **percorso** simboli per caricare da una directory in cui sono stati precedentemente archiviati i simboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Per caricare simboli di Framework utilizzando la finestra Stack di chiamate  
  
1. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse su un frame per il quale non sono caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).  
  
2. Scegliere **Carica simboli da** , quindi fare clic su server dei simboli **Microsoft** o **percorso simboli**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
