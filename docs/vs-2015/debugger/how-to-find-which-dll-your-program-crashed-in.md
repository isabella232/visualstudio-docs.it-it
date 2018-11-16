---
title: 'Procedura: individuare la DLL del programma arrestato in modo anomalo | Microsoft Docs'
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
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7af6940de5bd4e39451f44176f5c15d2e8b4548
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778397"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Procedura: individuare la DLL che ha causato l'arresto anomalo del programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto. Se si verifica un arresto anomalo del sistema in una DLL esterna al programma, è possibile identificare il percorso usando il **moduli** finestra.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli  
  
1.  Annotare l'indirizzo in cui si è verificato l'arresto.  
  
2.  Nel **eseguire il Debug** menu, scegliere **Windows**, fare clic su **moduli**.  
  
3.  Nel **moduli** finestra, trovare il **indirizzo** colonna. Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.  
  
4.  Scegliere il **indirizzo** nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.  
  
5.  Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.  
  
6.  Esaminare i **Name** e **percorso** colonne per visualizzare il nome della DLL e il percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: eseguire il Debug di DLL Native](../debugger/how-to-debug-native-dlls.md)   
 [Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)





