---
title: Comando Elenca moduli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26c2a2c07e09863c3320c3c69b8cc093bdf39466
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790033"
---
# <a name="list-modules-command"></a>Comando Elenca moduli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Elenca i moduli disponibili per il processo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parametri  
 /Address:`yes|no`  
 Facoltativo. Specifica se visualizzare gli indirizzi di memoria dei moduli. Il valore predefinito è `yes`.  
  
 /Name:`yes|no`  
 Facoltativo. Specifica se visualizzare i nomi dei moduli. Il valore predefinito è `yes`.  
  
 /Order:`yes|no`  
 Facoltativo. Specifica se visualizzare l'ordine dei moduli. Il valore predefinito è `no`.  
  
 /Path:`yes|no`  
 Facoltativo. Specifica se visualizzare i percorsi dei moduli. Il valore predefinito è `yes`.  
  
 /Process:`yes|no`  
 Facoltativo. Specifica se visualizzare i processi dei moduli. Il valore predefinito è `no`.  
  
 /SymbolFile:`yes|no`  
 Facoltativo. Specifica se visualizzare i file dei simboli dei moduli. Il valore predefinito è `no`.  
  
 /SymbolStatus:`yes|no`  
 Facoltativo. Specifica se visualizzare lo stato dei simboli dei moduli. Il valore predefinito è `yes`.  
  
 /Timestamp:`yes|no`  
 Facoltativo. Specifica se visualizzare il timestamp dei moduli. Il valore predefinito è `no`.  
  
 /Version:`yes|no`  
 Facoltativo. Specifica se visualizzare le versioni dei moduli. Il valore predefinito è `no`.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono elencati i nomi dei moduli, gli indirizzi e i timestamp per il processo corrente.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Procedura: Usare la finestra Moduli](../../debugger/how-to-use-the-modules-window.md)
