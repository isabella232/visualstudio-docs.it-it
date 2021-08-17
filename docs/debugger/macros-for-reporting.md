---
title: Macro per la creazione di | Microsoft Docs
description: Informazioni sulle macro di debug _RPTn e _RPTFn in CRTDBG. H e sulla creazione di macro di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c3479483b5baf1bef9d6001ff5a8bffca53a675bd9d50d916d7241c8e67ee96c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453120"
---
# <a name="macros-for-reporting"></a>Macro per la creazione di rapporti
Per il debug, è possibile **usare _RPTn** e **_RPTFn** macro, definite in CRTDBG. H, per sostituire l'uso `printf` di istruzioni . Non è necessario chiuderli in #ifdef perché scompaiono automaticamente nella build  di rilascio quando _DEBUG non è definito.

|Macro|Descrizione|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Genera una stringa di messaggio e da zero a quattro argomenti. Per **_RPT1** da **_RPT4**, la stringa di messaggio viene utilizzata come stringa di formattazione di tipo printf per gli argomenti.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Come **_RPTn**, ma queste macro generano anche il nome file e il numero di riga in cui si trova la macro.|

 Si consideri l'esempio seguente:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Questo codice invia a **stdout** i valori di `someVar` e `otherVar`. È possibile utilizzare la chiamata di `_RPTF2` che segue per restituire questi stessi valori nonché il nome file e il numero di riga:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

È possibile che una particolare applicazione necessita di report di debug che le macro fornite con la libreria di runtime C non forniscono. In questi casi, è possibile scrivere una macro progettata in modo specifico per soddisfare i propri requisiti. In uno dei file di intestazione, ad esempio, è possibile includere un codice simile al seguente per definire una macro denominata **ALERT_IF2**:

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 Una chiamata a **ALERT_IF2** eseguire tutte le funzioni del **codice printf:**

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 È possibile modificare facilmente una macro personalizzata per segnalare più o meno informazioni a destinazioni diverse. Questo approccio è particolarmente utile quando i requisiti di debug si evolvono.

## <a name="see-also"></a>Vedi anche
- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)
