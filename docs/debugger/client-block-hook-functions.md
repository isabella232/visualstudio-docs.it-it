---
title: Funzioni Hook del blocco client | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 900e8db238ee26e0a7015c2acc1741a1917c8cb3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609020"
---
# <a name="client-block-hook-functions"></a>Funzioni hook del blocco client
Se si desidera convalidare o inserire in report il contenuto dei dati memorizzati in blocchi `_CLIENT_BLOCK`, sarà possibile scrivere una funzione specificamente per tale scopo. Tale funzione dovrà avere un prototipo analogo al seguente, come definito in CRTDBG.H:

```cpp
void YourClientDump(void *, size_t)
```

 In altri termini, la funzione hook dovrà accettare un puntatore **void** all'inizio dell'argomento del blocco di allocazione, insieme a un valore di tipo **size_t** che indica la dimensione dell'allocazione, e restituire un valore `void`. Non esistono altre limitazioni al contenuto.

 Dopo aver installato la funzione hook mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), essa verrà chiamata ogni volta che viene effettuato il dump di un blocco `_CLIENT_BLOCK`. Sarà quindi possibile utilizzare [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) per ottenere informazioni sul tipo o sul sottotipo dei blocchi di cui è stato effettuato il dump.

 Il puntatore alla funzione che viene passato a `_CrtSetDumpClient` è del tipo **_CRT_DUMP_CLIENT**, come definito in CRTDBG.H:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Vedere anche

- [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)
- [Esempio di crt_dbg2](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)