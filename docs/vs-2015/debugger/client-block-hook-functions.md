---
title: Funzioni Hook del blocco client | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702329"
---
# <a name="client-block-hook-functions"></a>Funzioni hook del blocco client
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si desidera convalidare o inserire in report il contenuto dei dati memorizzati in blocchi `_CLIENT_BLOCK`, sarà possibile scrivere una funzione specificamente per tale scopo. Tale funzione dovrà avere un prototipo analogo al seguente, come definito in CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 In altri termini, la funzione hook dovrà accettare un puntatore **void** all'inizio dell'argomento del blocco di allocazione, insieme a un valore di tipo **size_t** che indica la dimensione dell'allocazione, e restituire un valore `void`. Non esistono altre limitazioni al contenuto.  
  
 Dopo aver installato la funzione hook mediante [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), essa verrà chiamata ogni volta che viene effettuato il dump di un blocco `_CLIENT_BLOCK`. Sarà quindi possibile utilizzare [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) per ottenere informazioni sul tipo o sul sottotipo dei blocchi di cui è stato effettuato il dump.  
  
 Il puntatore alla funzione che viene passato a `_CrtSetDumpClient` è del tipo **_CRT_DUMP_CLIENT**, come definito in CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio di crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
