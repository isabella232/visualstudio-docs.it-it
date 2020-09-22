---
title: 'Procedura: eseguire il debug da un progetto di DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839951"
---
# <a name="how-to-debug-from-a-dll-project"></a>Procedura: eseguire il debug da un progetto di DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per avviare il debug di un progetto DLL, è necessario specificare l'applicazione chiamante nelle proprietà del progetto. Il layout e il contenuto delle pagine delle proprietà di C++ sono diversi da quelli delle pagine delle proprietà di C# e Visual Basic.  
  
 Se una DLL gestita viene chiamata da codice nativo e si vuole eseguire il debug di entrambi, specificarlo nelle proprietà del progetto. Per altre informazioni, vedere [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Non è possibile specificare un'applicazione chiamante esterna nelle edizioni Express di Visual Studio. È necessario aggiungere un progetto eseguibile alla soluzione, impostarlo come progetto di avvio e chiamare i metodi nella DLL dal progetto eseguibile.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Per specificare l'applicazione chiamante in un progetto C++  
  
1. Fare clic con il pulsante destro del mouse sul nodo del progetto nella **Esplora soluzioni** e scegliere **Proprietà**. Passare alla scheda **debug** .  
  
2. Assicurarsi che il campo **Configurazione** nella parte superiore della finestra sia impostato su **Debug**.  
  
3. Passare a **proprietà di configurazione/debug**.  
  
4. Nell'elenco **debugger da avviare** scegliere **debugger Windows locale** o **debugger Windows remoto**.  
  
5. Nella casella **comando** o **comando remoto** aggiungere il nome percorso completo dell'applicazione.  
  
6. Aggiungere tutti gli argomenti del programma necessari nella casella **Argomenti del comando**.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Per specificare l'applicazione chiamante in un progetto C# o Visual Basic  
  
1. Fare clic con il pulsante destro del mouse sul nodo del progetto nella **Esplora soluzioni** e scegliere **Proprietà**. Passare alla scheda **debug** .  
  
     Selezionare **Avvia programma esterno**e aggiungere il nome percorso completo del programma da eseguire.  
  
     Se è necessario aggiungere gli argomenti della riga di comando del programma esterno, aggiungerli nel campo **argomenti della riga di comando** .  
  
2. È anche possibile chiamare un'applicazione sotto forma di URL. Potrebbe essere necessario eseguire questa operazione se si esegue il debug di una DLL gestita usata da un'applicazione ASP.NET locale.  
  
     In **azione di avvio**selezionare il pulsante **di opzione Avvia browser in URL:** e compilare l'URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Per avviare il debug dal progetto DLL  
  
1. Impostare i punti di interruzione necessari.  
  
2. Avviare il debug (premere F5, fare clic sulla freccia verde oppure fare clic su **debug/Avvia debug**).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di progetti DLL](../debugger/debugging-dll-projects.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
