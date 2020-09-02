---
title: 'Procedura: eseguire il debug di DLL native | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702676"
---
# <a name="how-to-debug-native-dlls"></a>Procedura: eseguire il debug di DLL native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il debug di una DLL può essere avviato:  
  
- Dal progetto utilizzato per la creazione dell'eseguibile che chiama la DLL.  
  
  \- - oppure -  
  
- Dal progetto stesso utilizzato per la creazione della DLL.  
  
  Se si dispone del progetto utilizzato per la creazione dell'eseguibile, iniziare il debug da tale progetto. Sarà quindi possibile aprire un file di origine relativo alla DLL e impostare i punti di interruzione in tale file, anche se non appartiene al progetto utilizzato per la creazione dell'eseguibile. Per altre informazioni, vedere [Punti di interruzione](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Se il debug viene avviato dal progetto che crea la DLL, è necessario specificare l'eseguibile che si desidera utilizzare per il debug della DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Per specificare un eseguibile per la sessione di debug  
  
1. In **Esplora soluzioni**selezionare il progetto che crea la dll.  
  
2. Scegliere**pagine delle proprietà**dal menu **Visualizza** .  
  
3. Nella finestra di dialogo **pagine delle proprietà** aprire la cartella **proprietà di configurazione** e selezionare la categoria **debug** .  
  
4. Nella casella **comando** specificare il nome del percorso per il contenitore. Ad esempio, C:\Programmi\Applicazione\APP.EXE.  
  
5. Nella casella **argomenti comando** specificare gli eventuali argomenti necessari per l'eseguibile.  
  
   Se non si specifica il file eseguibile nella finestra di dialogo**pagine delle proprietà** del _progetto_, quando si avvia il debug viene visualizzata la finestra [di dialogo eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
