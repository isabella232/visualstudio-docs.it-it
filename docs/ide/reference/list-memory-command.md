---
title: Comando Elenca memoria | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae04c23a986107125edc9be149d6317a05c5b58a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="list-memory-command"></a>Comando Elenca memoria
Visualizza il contenuto dell'intervallo di memoria specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Parametro facoltativo. L'indirizzo di memoria da cui iniziare la visualizzazione della memoria.  
  
## <a name="switches"></a>Opzioni  
 /ANSI&#124;Unicode  
 Parametro facoltativo. Visualizza la memoria come caratteri corrispondenti ai byte di memoria, ANSI o Unicode.  
  
 /Count:`number`  
 Parametro facoltativo. Determina il numero di byte di memoria da visualizzare, a partire da `expression`.  
  
 /Format:`formattype`  
 Parametro facoltativo. Tipo di formato per la visualizzazione di informazioni sulla memoria nella finestra **Memoria**; può essere OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bit) o Double (64 bit). Se viene usato il formato OneByte, `/Unicode` non è disponibile.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Parametro facoltativo. Specifica il formato per la visualizzazione dei numeri: con segno, senza segno o esadecimale.  
  
## <a name="remarks"></a>Note  
 Invece di scrivere un comando **Debug.ListMemory** completo con tutte le opzioni, è possibile richiamare il comando tramite alias predefiniti con alcune opzioni preimpostate su valori specificati. Ad esempio, anziché immettere:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 è possibile scrivere:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Di seguito viene riportato un elenco degli alias disponibili per il comando **Debug.ListMemory**:  
  
|Alias|Comandi e opzioni|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)