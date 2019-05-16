---
title: 'Procedura: Individuare la DLL del programma arrestato in modo anomalo | Microsoft Docs'
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
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703622"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Procedura: Trovare la DLL che ha causato l'arresto anomalo del programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto. Se si verifica un arresto anomalo in una DLL esterna al programma, è possibile identificarne la posizione utilizzando la finestra **Moduli**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli  
  
1. Annotare l'indirizzo in cui si è verificato l'arresto.  
  
2. Scegliere **Finestre** dal menu **Debug**, quindi **Moduli**.  
  
3. Nella finestra **Moduli** individuare la colonna **Indirizzo**. Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.  
  
4. Fare clic sul pulsante **Indirizzo** nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.  
  
5. Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.  
  
6. Nelle colonne **Nome** e **Percorso** cercare il nome e il percorso della DLL.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire il debug di DLL Native](../debugger/how-to-debug-native-dlls.md)   
 [Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)
