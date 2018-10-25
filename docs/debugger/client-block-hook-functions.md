---
title: Funzioni Hook del blocco client | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9de7c0533d3ea55e7b78ca645735a60f84e66df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938019"
---
# <a name="client-block-hook-functions"></a>Funzioni hook del blocco client
Se si desidera convalidare o inserire in report il contenuto dei dati memorizzati in blocchi `_CLIENT_BLOCK`, sarà possibile scrivere una funzione specificamente per tale scopo. Tale funzione dovrà avere un prototipo analogo al seguente, come definito in CRTDBG.H:  

```cpp
void YourClientDump(void *, size_t)  
```  

 In altre parole, la funzione di hook dovrà accettare un **void** puntatore all'inizio del blocco di allocazione, insieme a un **size_t** tipo valore che indica la dimensione dell'allocazione e restituire `void`. Non esistono altre limitazioni al contenuto.  

 Dopo aver installato la funzione hook mediante [CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), verrà chiamato ogni volta che un `_CLIENT_BLOCK` dump di blocco. È quindi possibile usare [CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) per ottenere informazioni sul tipo o sul sottotipo dei blocchi di dump;.  

 Il puntatore alla funzione che viene passato a `_CrtSetDumpClient` JE typu **CRT_DUMP_CLIENT**, come definito in CRTDBG. H:  

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  

## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni Hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio crt_dbg2](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
