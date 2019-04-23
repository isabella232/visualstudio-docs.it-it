---
title: Comando Elenca registri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f9eaa1299ec49cf20713723e822f8fc641401d8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658539"
---
# <a name="list-registers-command"></a>Comando Elenca registri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente di visualizzare il valore dei registri selezionati e di modificare l'elenco dei registri da visualizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Opzioni  
 /Display [{`register`&#124;`registerGroup`}...]  
 Consente di visualizzare i valori dell'oggetto `register` o `registerGroup` specificato. Se non è stato specificato alcun oggetto `register` o `registerGroup`, viene visualizzato l'elenco predefinito dei registri. Se non viene specificata alcuna opzione, il comportamento è lo stesso. Ad esempio:  
  
 `Debug.ListRegisters /Display eax`  
  
 equivale a  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Consente di visualizzare tutti i gruppi di registri nell'elenco.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Aggiunge uno o più valori `register` o `registerGroup` all'elenco.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Rimuove uno o più valori `register` o `registerGroup` dall'elenco.  
  
## <a name="remarks"></a>Note  
 L'alias `r` può essere usato al posto di `Debug.ListRegisters`.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene usato l'alias di `Debug.ListRegisters` `r` per visualizzare i valori del gruppo di registri `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Informazioni di base sul debug: Finestra registri](../../debugger/debugging-basics-registers-window.md)   
 [Procedura: Usare la finestra Registri](../../debugger/how-to-use-the-registers-window.md)
