---
title: Comando Elenca disassembly | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cbdc3ee566135fe86301deefe1e8be8db431f9f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256659"
---
# <a name="list-disassembly-command"></a>Comando Elenca disassembly
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Opzioni  
 Ogni opzione può essere richiamata usando la forma completa o una forma breve.  
  
 /count: `number` [or] /c: `number` [or] /length: `number` [or] /l: `number`  
 Facoltativo. Numero di istruzioni da visualizzare. Il valore predefinito è 8.  
  
 /endaddress: `expression` [or] /e: `expression`  
 Facoltativo. Indirizzo in corrispondenza del quale interrompere il disassembly.  
  
 /codebytes:`yes`&#124;`no` [or] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare i byte di codice. Il valore predefinito è `no`.  
  
 /source:`yes`&#124;`no` [or] /s:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare il codice sorgente. Il valore predefinito è `no`.  
  
 /symbolnames:`yes`&#124;`no` [or] /names:`yes`&#124;`no` [or] /n:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare i nomi dei simboli. Il valore predefinito è `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Facoltativo. Abilita la visualizzazione dei numeri di riga associati al codice sorgente. L'opzione /source deve avere un valore di `yes` per usare l'opzione /linenumbers.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



