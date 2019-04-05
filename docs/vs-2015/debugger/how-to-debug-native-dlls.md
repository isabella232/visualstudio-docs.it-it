---
title: 'Procedura: Eseguire il debug di DLL Native | Microsoft Docs'
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
ms.openlocfilehash: ffc4f0b58bacdc71439a89dce711575a103c71cf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964335"
---
# <a name="how-to-debug-native-dlls"></a>Procedura: Eseguire il debug di DLL Native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il debug di una DLL può essere avviato:  
  
- Dal progetto utilizzato per la creazione dell'eseguibile che chiama la DLL.  
  
  \- oppure -  
  
- Dal progetto stesso utilizzato per la creazione della DLL.  
  
  Se si dispone del progetto utilizzato per la creazione dell'eseguibile, iniziare il debug da tale progetto. Sarà quindi possibile aprire un file di origine relativo alla DLL e impostare i punti di interruzione in tale file, anche se non appartiene al progetto utilizzato per la creazione dell'eseguibile. Per altre informazioni, vedere [Punti di interruzione](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Se il debug viene avviato dal progetto che crea la DLL, è necessario specificare l'eseguibile che si desidera utilizzare per il debug della DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Per specificare un eseguibile per la sessione di debug  
  
1. Nelle **Esplora soluzioni**, selezionare il progetto che crea la DLL.  
  
2. Dal **View** menu, scegliere**pagine delle proprietà**.  
  
3. Nel **pagine delle proprietà** finestra di dialogo, aprire il **le proprietà di configurazione** cartella e selezionare il **debug** categoria.  
  
4. Nel **comando** , specificare il nome del percorso per il contenitore. Ad esempio, C:\Programmi\Applicazione\APP.EXE.  
  
5. Nel **argomenti del comando** , specificare gli argomenti necessari per il file eseguibile.  
  
   Se non si specifica il file eseguibile nel _Project_**pagine delle proprietà** della finestra di dialogo il [eseguibile per la finestra di dialogo di sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md) viene visualizzata quando si avvia il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
