---
title: 'Procedura: eseguire il Debug da un progetto di DLL | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7b38ac26a07965dc5408c1da1c655a010b6a788
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266188"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Procedura: eseguire il Debug da un progetto DLL in Visual Studio

Un modo per un progetto di DLL di debug consiste nello specificare app chiamante nelle proprietà del progetto DLL. È quindi possibile avviare il debug dal progetto di DLL stessa. Per usare questo metodo, l'app deve chiamare la stessa DLL nella stessa posizione di quello che configurare. Se l'app Trova e carica una versione diversa della DLL, tale versione non includerà i punti di interruzione. Per altri metodi di debug di DLL, vedere [progetti di DLL di debug](../debugger/debugging-dll-projects.md).
  
Se l'app gestita chiama una DLL nativa o l'app nativa chiama una DLL gestita, è possibile eseguire il debug della DLL sia app chiamante. Per altre informazioni, vedere [procedura: eseguire il Debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).   

I progetti DLL nativi e gestiti hanno impostazioni diverse per specificare le app. 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Specificare un'app chiamante in un progetto DLL native  
  
1. Selezionare il progetto di DLL C++ in **Esplora soluzioni**. Selezionare il **delle proprietà** icona, premere **Alt**+**invio**, o fare clic e scegliere **proprietà**.
   
1. Nel  **\<progetto > pagine delle proprietà** finestra di dialogo casella, assicurarsi che il **Configuration** campo nella parte superiore della finestra è impostato su **Debug**. 
   
1. Selezionare **le proprietà di configurazione** > **debug**.  
   
1. Nel **Debugger da avviare** elenco, scegliere **Debugger Windows locale** oppure **Debugger Windows remoto**.  
   
1. Nel **comandi** oppure **comando remoto** , aggiungere il percorso completo e il nome dell'applicazione chiama, ad esempio un *.exe* file.
   
   ![Finestra delle proprietà di debug](../debugger/media/dbg-debugging-properties-dll.png "finestra delle proprietà di Debug")  
   
1. Aggiungere gli argomenti del programma necessari per il **argomenti del comando** casella.  
   
1. Scegliere **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Specificare un'app chiamante in un progetto di DLL gestita  
  
1. Selezionare il progetto di DLL di Visual Basic o c# in **Esplora soluzioni**. Selezionare il **delle proprietà** icona, premere **Alt**+**invio**, o fare clic e scegliere **proprietà**.
   
1. Assicurarsi che il **Configuration** campo nella parte superiore della finestra è impostato su **Debug**.
   
1. Sotto **azione di avvio**:
   
   - Per la DLL di .NET Framework, selezionare **Avvia programma esterno**e aggiungere il percorso completo e il nome dell'app chiamante.
     
   - In alternativa, selezionare **avvia il browser con URL** e specificare l'URL di un'app ASP.NET locale. 
   
   - Per le DLL di .NET Core, il **Debug** pagina delle proprietà è diversa. Selezionare **eseguibile** dal **Launch** elenco a discesa e quindi aggiungere il percorso completo e il nome dell'app chiamante nel **eseguibile** campo. 
   
1. Aggiungere tutti gli argomenti della riga di comando necessari nel **argomenti della riga di comando** oppure **argomenti dell'applicazione** campo.
   
   ![Finestra proprietà di Debug c#](../debugger/media/dbg-debugging-properties-dll-csharp.png "finestra proprietà di Debug c#") 
   
1. Uso **File** > **Salva elementi selezionati** oppure **Ctrl**+**S** per salvare le modifiche.

## <a name="debug-from-the-dll-project"></a>Eseguire il debug dal progetto di DLL  
 
1. Impostare punti di interruzione nel progetto DLL.

1. Fare clic sul progetto DLL e scegliere **imposta come progetto di avvio**. 

1. Assicurarsi che il **soluzioni Configuration** campo è impostato su **Debug**. Premere **F5**, fare clic su verde **avviare** freccia oppure selezionare **Debug** > **Avvia debug**.

Se il debug non raggiungere i punti di interruzione, verificare che la DLL di output (per impostazione predefinita, il  *\<progetto > \Debug* cartella) è la posizione che chiama l'app chiama.
  
## <a name="see-also"></a>Vedere anche  
 [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)   
 [Impostazioni di progetto per le configurazioni di debug c#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)